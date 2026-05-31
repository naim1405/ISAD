# System Design — Nextstepbd

This document gives an in-depth technical design for the three systems we will implement to solve the identified problems. The content is detailed enough to guide implementation teams: component diagrams (text), data model, integration patterns, pipelines, security and deployment recommendations, and acceptance criteria.

---

## 0. Goals and Constraints

Goals
- Provide a single source of truth for business records (customers, projects, requirements, tasks).
- Capture authoritative approvals and decisions from informal channels without forcing users to change habits.
- Make collaboration structured, auditable and automatable using off-the-shelf collaboration tools.
- Ensure safe, repeatable delivery with CI/CD, monitoring, and incident workflows.

Constraints
- Third-party APIs (WhatsApp Business) have registration, template and rate limits.
- Minimal disruption to user workflows — adopt human-in-loop and capture shortcuts.
- Limited initial engineering bandwidth — prefer buy vs build where sensible.
- Compliance: PII must be handled carefully (redaction, RBAC, retention).

Assumed Technology Stack (recommended)
- Backend & API: PostgreSQL, Hasura (GraphQL) or Node/Go + GraphQL/REST
- Integration/Orchestration: n8n (self-hosted) or custom microservices
- Queue: RabbitMQ or Kafka (or managed alternatives)
- Storage: PostgreSQL for canonical data; S3 for attachments
- Auth: Keycloak or Auth0 (SSO) with JWT
- DevOps: GitHub Actions + ArgoCD/Flux for k8s, Terraform for infra
- Observability: Prometheus + Grafana, Loki/ELK for logs, Jaeger for tracing
- Error tracking: Sentry
- Secrets: Vault or cloud KMS
- Collaboration tool: Jira/ClickUp/Notion (SaaS)

---

## 1. System A — Central Integration & Data Platform

### 1.1 Objectives
- Ingest data from multiple sources (chat, sheets, email, code repo) and normalize into canonical entities.
- Provide an authoritative API for reading/writing records.
- Maintain provenance and audit logs for compliance.
- Offer operator tools for human-in-loop confirmations and reconciliations.

### 1.2 High-level Architecture (components)
- Connectors / Adapters: source-specific adapters (WhatsApp/Twilio, Google Sheets API, GitHub webhooks, IMAP/email, manual CSV upload).
- Ingest Gateway: small service that receives connector events, validates, and enqueues them.
- Processing Queue: durable queue (Rabbit/Kafka) for decoupling ingestion and processing.
- Parser & Enricher Service: applies rules/NLP to extract intents/entities, normalizes data, suggests mappings.
- Dedupe & Merge Engine: identifies duplicates via heuristics (fuzzy name, phone/email match) and applies merge or flags for operator.
- Human-in-Loop Review UI: operator queue for ambiguous or sensitive items (web UI) with quick confirm/merge actions.
- Canonical Store (DB): PostgreSQL with normalized schema and audit tables.
- API Layer: GraphQL/REST layer (Hasura or custom) exposing CRUD + query + event endpoints.
- Event Bus / Outbound Integrations: emits events (RequirementCreated, CustomerMerged) for other systems.
- Admin & Monitoring Dashboard: health, connector status, ingestion metrics, error queue.

Textual Component Diagram
- [Connectors] -> Ingest Gateway -> [Queue] -> Parser/Enricher -> Dedupe Engine -> Canonical DB
- Canonical DB -> API Layer -> Collaboration / DevOps / Reports
- Parser/Enricher -> Human-in-loop UI -> (confirm/modify) -> Canonical DB
- Canonical DB -> Event Bus -> Collaboration Tool Integration Service

### 1.3 Canonical Data Model (core entities)
- Customer: id, name, primary_email, phone, address, external_ids (sheet_id, github_org), created_by, created_at
- Project: id, name, customer_id, status, start_date, end_date
- Requirement: id, project_id, title, description, source (message_id or sheet_row_id), status, approved_by, approved_at, confidence_score
- Task: id, requirement_id, title, assignee_id, status, external_ticket_id
- SourceMessage: id, source_type (whatsapp,sheet,github,email), raw_text, parsed_text, timestamp, author, source_meta
- AuditLog: id, entity_type, entity_id, action, actor, timestamp, details
- User: id, name, roles, external_auth_id

Notes: include indices on external_ids and timestamps for fast searching; use JSONB for flexible metadata per source.

### 1.4 Ingestion & Processing Pipeline (detailed)
1. Connector emits event to Ingest Gateway (HTTP webhook or push).
2. Gateway validates payload, attaches metadata (received_at, connector_id), and writes to Queue with an idempotency key.
3. Parser/Enricher worker consumes event:
   - Run lightweight NLP rules (regex + entity extraction) to detect intents like "approval", "new requirement", "bug report".
   - Map fields to candidate canonical entities (e.g., title -> requirement.title; phone -> customer.phone).
   - Compute confidence_score; if below threshold or containing sensitive keywords, mark as `requires_review`.
4. Dedupe engine checks for matches (email/phone/name fuzzy match): if match is confident, link to existing entity; if ambiguous, flag for operator.
5. If `requires_review` = true -> create Operator Task (in Human UI) with suggested mappings.
6. On operator confirm, persist canonical entities in DB, write AuditLog, publish event RequirementCreated.
7. If automatic, persist and publish event.
8. Outbound Integration Service subscribes to events and creates/updates tasks in Collaboration tool via its API.

Idempotency and ordering: use event ids and idempotency keys for connectors to avoid duplicate creations; use sequence numbers or timestamps for message ordering when relevant.

### 1.5 Connectors — specifics
- WhatsApp: integrate via Twilio or 360dialog Business API. Limitations: template messages for outbound, rate limits. Strategy: inbound messages are accepted; use quick-reply templates for confirmations where possible; otherwise send capture UI link for PM/operator.
- Google Sheets: use Sheets API to monitor specific ranges; support manual reconciliation runs.
- GitHub: subscribe to webhooks for issues, PR comments; map mentions like "acceptance" to requirement approvals.
- Email: IMAP polling or webhook forwarding, with parsing for structured content.
- Manual CSV/Upload: for migration or ad-hoc imports.

Retries and error handling: connectors should implement retries with exponential backoff; failed items move to error queue and visible on admin dashboard.

### 1.6 APIs & Integration Patterns
- API endpoints: /graphql or REST for entities; /webhooks for connector callbacks; /events for consuming services.
- Authentication: issue JWTs via SSO (Keycloak) with scopes/roles.
- Webhooks: outbound webhook with HMAC signature for Collaboration integration.
- Rate limiting and batching: allow batch imports for Sheets; batch webhook deliveries when integration is slow.

### 1.7 Consistency & Conflict Resolution
- Model: eventual consistency with provenance. Show source and confidence on each record.
- Conflict policy: if two sources disagree, do not auto-overwrite high-confidence existing values without operator confirmation. Provide a merge UI showing differences and provenance.

### 1.8 Security & Compliance
- PII: detect via simple classifiers and redact stored raw_text if necessary; store redacted_text + secure reference to encrypted full content if needed.
- Encryption: TLS in transit; at-rest encryption (DB + S3 encryption); secrets stored in Vault.
- RBAC: implement role-based access controls at API and UI layers; limit who can view or un-redact PII.
- Audit: every action (create/update/view) has AuditLog entry with actor and timestamp.

### 1.9 Observability
- Metrics: ingestion rate, processing lag, connector errors, review queue size.
- Logs: structured logs with trace ids.
- Tracing: pass request IDs from connector through processing pipeline.
- Alerts: alert when queue depth grows or connectors fail.

### 1.10 Backups & Disaster Recovery
- DB backups (daily snapshot + WAL archiving), S3 lifecycle.
- Recovery RTO/RPO targets set per business needs.

### 1.11 Testing strategy
- Unit tests for parser rules.
- Contract tests for connectors.
- Integration tests with mock connectors.
- End-to-end tests using test workspace and a staging central DB.

### 1.12 Deployment & Scaling
- Deploy on k8s with horizontal autoscaling for workers.
- Use managed queue if available to reduce ops.
- Scale connectors separately from parser workers.

### 1.13 Estimated effort (MVP)
- 6–10 weeks: core schema, API, 2 connectors (Sheets, GitHub), parser/enricher, operator UI, basic RBAC/audit.

---

## 2. System B — Collaboration & Workflow System (SaaS integration)

### 2.1 Objectives
- Provide the human-facing workspace for tasks, approvals, and documents using established tools.
- Automate routine workflows and reduce PM bottleneck.
- Keep every task connected to canonical Central records for reporting and traceability.

### 2.2 Architecture (components)
- Chosen SaaS: Jira/ClickUp/Linear (project config, boards, automation)
- Integration Service: small bridge service that maps Central entity IDs to SaaS issue IDs and syncs events/status.
- Template Library: configuration of templates and automation rules inside the SaaS.
- Linker/Enricher: adds links and metadata to tasks showing canonical info (Requirement ID, Customer, origin message link).
- Webhook handlers: process events from SaaS (status changes, comments, attachments) and update Central where needed.

Textual Component Diagram
- Central DB (Requirement) <-> Integration Service <-> SaaS (Issue/Task)
- SaaS events -> Integration Service -> Central API (status, approvals, comments)

### 2.3 Integration Patterns
- Create-on-event: when Central publishes RequirementCreated, Integration Service creates a new issue in SaaS with mapped fields.
- Status-sync: when issue moves to Done/Accepted, SaaS sends webhook to Integration Service, which updates Requirement.status in Central.
- Comment-linking: comments/attachments posted to SaaS task include a link and are recorded in Central as SourceMessage reference.
- One-way vs two-way sync: start with central -> SaaS (create and update) and SaaS -> Central for status/approval only. Avoid full field-level two-way sync initially to reduce conflict complexity.

### 2.4 Data mapping and schema
- Maintain mapping table: central_id <-> saas_issue_id, with last_sync_at and last_sync_hash.
- Field mapping example: Requirement.title -> Issue.summary; Requirement.description -> Issue.description; Requirement.approved_by -> custom field.

### 2.5 Automation & Templates
- Use native SaaS automation to create sets of tasks on issue creation, set SLA due dates, and auto-assign based on team/skills tags.
- Implement lightweight capacity-based assignment in integration service if SaaS automation can't meet needs.

### 2.6 UX Flows
- Capture from chat: user clicks "Create requirement" button on a message (or operator does), central records created, Integration Service opens an issue in SaaS and posts link back to chat.
- Approval: client approves via SaaS comment; webhook updates Central.requirement.approved_at and emits event for billing.

### 2.7 Security and Access
- Use OAuth for SaaS API access with workspace admin account. Use SSO (Keycloak/Auth0) for user login where possible.
- Map Central roles to SaaS project roles where feasible (viewer/editor/admin) to avoid duplicate permission setups.

### 2.8 Error handling and reconciliation
- Integration Service keeps failed webhook deliveries in a retry queue; manual retry UI for admins.
- Reconciliation job runs nightly to ensure mapping table and statuses are consistent; report discrepancies.

### 2.9 Observability
- Monitor integration latency, webhook failures, template execution errors.

### 2.10 Deployment & Ops
- Integration Service is small, deployable on k8s or serverless; leverage SaaS rate limits handling.

### 2.11 Estimated effort
- 4–8 weeks to configure SaaS, build Integration Service, create templates, pilot with one project.

---

## 3. System C — DevOps, QA & Observability Platform

### 3.1 Objectives
- Automate testing and deployments to reduce manual errors.
- Detect and resolve incidents quickly with proper alerts and runbooks.
- Provide operational telemetry to Central for reporting.

### 3.2 Architecture (components)
- Source Control: GitHub/GitLab
- CI: GitHub Actions / GitLab CI for build/test
- Artifact Registry: Docker registry or cloud artifact store
- IaC: Terraform for infra provisioning
- CD: ArgoCD / Flux (k8s) or cloud deployment pipelines
- Monitoring: Prometheus + Grafana
- Logging: Loki / ELK stack
- Tracing: Jaeger / OpenTelemetry
- Error Tracking: Sentry
- Alerting & Paging: PagerDuty or Opsgenie
- Incident Management: integrates with Collaboration (create incident ticket automatically)

Textual Component Diagram
- Developer -> PR -> CI (tests) -> Build artifacts -> CD -> Staging -> Health checks -> Production
- Production -> Observability -> Alerts -> Collaboration Incident -> Central (link to affected Requirement/Task)

### 3.3 Pipelines and Workflows
- PR pipeline: lint -> unit tests -> static analysis -> build artifacts -> publish to registry.
- Merge gated by successful CI + required approvals.
- Staging deploy: auto-deploy to staging on merge to develop branch; run integration tests and smoke tests.
- Production deploy: manual approval or automated canary with health checks and automatic rollback.
- Rollback: safe rollback strategy via previous artifact or short-lived feature flags.

### 3.4 Observability & Incident Flow
- Instrument apps with metrics, logs and traces.
- Define SLOs and SLIs for key services; dashboards in Grafana.
- Alerts for SLO breaches go to PagerDuty and create an incident in Collaboration with links to logs and traces.
- On-call runbooks accessible from incident ticket; post-mortem templates stored in Collaboration.

### 3.5 Security & Compliance in Pipeline
- Secrets from Vault injected into runtime; do not store secrets in repo.
- Image scanning and dependency scanning in CI (Trivy, Snyk).
- Role separation: devs cannot push to production without approvals.

### 3.6 Integrations to Central & Collaboration
- Push deployment metadata (who, artifact, env, timestamp) to Central as events.
- When incidents reference a Requirement or Task, link incident ticket to those canonical IDs for traceability.

### 3.7 Testing strategy
- Unit, integration, contract tests.
- End-to-end tests in staging.
- Performance and load tests scheduled before major releases.

### 3.8 Deployment model
- Prefer k8s for service deployments for consistency; for small services, serverless (FaaS) can be used to reduce operational overhead.

### 3.9 Observability stack sizing & cost
- Use managed services for logs/metrics if budget allows; otherwise self-host but plan for storage and retention costs.

### 3.10 Estimated effort
- 6–10 weeks to set up pipelines, IaC for core infra, basic monitoring, and incident integration.

---

## 4. Cross-cutting Concerns

### 4.1 Authentication & Authorization
- SSO with Keycloak/Auth0. Central issues JWTs used by services.
- RBAC model stored in Central and enforced at API and UI.

### 4.2 Secrets Management
- Use Vault or cloud KMS. CI/CD pulls secrets at runtime only.

### 4.3 Data Retention & Privacy
- PII handling policy: redact by default; store encrypted blobs with restricted un-redaction.
- Retention policy implemented via scheduled jobs.

### 4.4 Observability & SLAs
- Define SLAs for ingestion (e.g., 99% within 1 minute for Sheets/GitHub; WhatsApp best-effort due to rate limits).

### 4.5 Backups & DR
- DB snapshots daily; WAL archiving; test restore procedures quarterly.

### 4.6 Cost considerations
- SaaS (Collaboration + monitoring) vs self-hosting trade-offs: SaaS faster to deliver but recurring cost.

---

## 5. Rollout Plan (detailed)

Phase 0 — Preparation (2 weeks)
- Register WhatsApp Business (if needed) and Twilio account.
- Provision SSO, Vault, k8s cluster, CI/CD.
- Define canonical schema and basic API contracts.

Phase 1 — Central MVP (6–8 weeks)
- Implement canonical DB + API.
- Build connectors: Google Sheets + GitHub webhooks.
- Implement Parser/Enricher with rule-based extraction.
- Build operator review UI and audit logging.
- Connect to Collaboration prototype (create issues on RequirementCreated).

Phase 2 — Collaboration Integration (4–6 weeks)
- Configure chosen SaaS (Jira/ClickUp) for teams.
- Build Integration Service for mapping and status-sync.
- Pilot with 1–2 projects.

Phase 3 — DevOps & Observability (6–8 weeks)
- Implement CI pipelines, staging deploys, production deploy script.
- Add monitoring, alerting, and incident integration to Collaboration.
- Run simulated incidents and drills.

Phase 4 — Expand connectors & governance (ongoing)
- Add WhatsApp connector with human-in-loop flows.
- Add email/IMAP and other sources.
- Implement data governance policies, retention, reports, and full training.

Parallel activities: training, documentation, migration of existing sheets to canonical store, and adoption metrics.

---

## 6. Acceptance Criteria & KPIs

Acceptance
- Canonical DB stores Requirement with provenance for 95% of tested sample inputs.
- Operator queue processes ambiguous items with median resolution time < 1 hour.
- Collaboration issues are created and status-synced for pilot projects.
- CI pipeline blocks PR merge on failing tests and deploys succeed with health checks.

KPIs
- Reduction in clarification cycles (measure via Collaboration comments) by 50% in pilot.
- Decrease in manual reconciliation tasks by 70% for billing-related sheets.
- Mean time to detect (MTTD) and mean time to recover (MTTR) measured for incidents.

---

## 7. Next steps (implementation artifacts)
- Define detailed ERD and migration scripts for canonical DB.
- Create connector contracts (payload schemas) and mock servers for testing.
- Build Parser/Enricher rule set and simple NLP pipeline (regex -> entity rules -> fallback to operator).
- Create Integration Service specs for chosen SaaS (Jira/ClickUp) APIs.
- Implement CI/CD templates and IaC modules for k8s + monitoring.


---

End of system design.

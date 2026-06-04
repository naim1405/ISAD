# Key Problems We Will Address

This document lists the five priority problems selected for the ISAD report. Each problem includes a concise description, an example from current practice, the impact, and affected stakeholders.

## 1. Fragmented Communication & Collaboration
- Description: Critical project decisions and approvals are exchanged via informal chat (WhatsApp) and not captured in a structured project system. Project Managers act as a single communication bridge for many flows.
- Example: A client confirms a requirement in WhatsApp; the confirmation is not recorded in the task tracker, leading to scope mismatch when developers implement features.
- Impact: Missed requirements, rework, client disputes, slowed delivery.
- Affected stakeholders: Project managers, developers, clients, QA.
- Evidence: `NextStepBD/05_problems/communication_issues.md`, `NextStepBD/05_problems/workflow_bottlenecks.md`.

## 2. System Fragmentation & Lack of Integration
- Description: Multiple disconnected tools (Google Sheets, GitHub, Email, WhatsApp) are used with no integration layer, forcing manual coordination and cross-referencing by staff.
- Example: Customer status is maintained in multiple Sheets and by messages in chat; reconciliations are manual and error-prone.
- Impact: Increased maintenance overhead, inconsistent data, and slower decision-making.
- Affected stakeholders: Operations, integrators, management.
- Evidence: `NextStepBD/05_problems/system_fragmentation.md`.

## 3. Data Management & Governance Problems
- Description: No single source of truth, frequent duplication of records, manual updates, and no formal data governance policies.
- Example: Two spreadsheets list different billing statuses for the same client resulting in an incorrect invoice being issued.
- Impact: Wrong business decisions, billing errors, and reporting inaccuracies.
- Affected stakeholders: Finance, management, clients, data consumers.
- Evidence: `NextStepBD/05_problems/data_management_problems.md`.

## 4. Security & Access Control Risks
- Description: Sensitive information (customer data, credentials) shared in informal channels; no organization-wide RBAC, auditing, or secrets handling.
- Example: Credentials or client PII are forwarded in WhatsApp groups; there is no audit trail of who accessed or modified records.
- Impact: Data breaches, regulatory non-compliance, reputational and legal risk.
- Affected stakeholders: Clients, legal, management, IT/security.
- Evidence: `NextStepBD/05_problems/security_risks.md`.

## 5. Scalability & Operational Bottlenecks
- Description: Manual processes, heavy reliance on a few key individuals (single points of failure), and long onboarding times hinder the ability to scale the team and projects.
- Example: The Project Manager must manually assign tasks and chase updates; when the PM is unavailable, progress stalls.
- Impact: Reduced throughput, slow project ramp-up, burnout and retention issues.
- Affected stakeholders: HR, team leads, project managers, developers.
- Evidence: `NextStepBD/05_problems/scalability_issues.md`, `NextStepBD/05_problems/workflow_bottlenecks.md`.

---

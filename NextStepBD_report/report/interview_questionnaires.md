# Interview Questions & Questionnaires

This file provides two sections: (1) Interview Questions — open, role-specific prompts for semi-structured interviews; and (2) Questionnaires — closed items for survey distribution.

---

## Interview Questions

### CEO
1. Can you describe the company's current strategic priorities for the next 12–24 months?
Answer: Over the next year or two, our primary focus is strengthening recurring revenue streams while improving the predictability and quality of delivery. Practically, this means investing selectively in tools and process improvements that reduce rework and late deliveries, piloting automation to relieve project managers of repetitive reconciliation tasks, and packaging a small set of services into repeatable product offerings that generate steadier income. We are conscious of cost and time-to-value, so early pilots should deliver measurable operational benefits within a few months.
2. What are the most important operational risks you see today?
Answer: The most pressing risks are fragmented information flows that lead to misaligned scope and billing, single-person knowledge dependencies, and the use of informal channels for sensitive client data. Fragmented records create disputes that take time to resolve and harm client trust; key-person dependencies create single points of failure when staff leave or are unavailable; and informal handling of PII or credentials raises legal and reputational exposure. Mitigations should therefore focus on reliable capture of approvals, shared knowledge practices, and stronger access controls.
3. How do you measure service delivery success and client satisfaction?
Answer: We track a mix of operational and customer-facing indicators: on-time delivery rates, a basic client satisfaction check after each engagement, the volume and severity of billing disputes, and the time PMs spend on reconciliation activities. Qualitative feedback from account leads also informs our assessment, especially where repeated clarifications or churn indicate deeper process issues. Over time I’d like these measures to be automated or surfaced on dashboards so we can act faster.
4. Which processes or tools do you think limit the company's ability to scale?
Answer: Reliance on spreadsheets and chat for approvals and record-keeping is a major limiter. Without canonical identifiers for clients and contracts and a reliable capture mechanism for approvals, we add headcount to preserve consistency rather than improving efficiency. Likewise, tools that require duplicate entry or do not integrate well force manual reconciliation work that does not scale.
5. How are decisions about investment in tools, integrations, and people made?
Answer: Decisions are made by weighing ROI against time-to-value and risk. For urgent pain points we prefer low-friction SaaS pilots to prove value quickly; for structural capabilities or compliance needs we consider funded internal or custom work. Larger expenditures typically require a sponsor-level approval and a clear business case showing cost savings or revenue protection.
6. How do you currently obtain evidence for client approvals, scope changes, or billing disputes?
Answer: Evidence today is ad hoc: threaded chats, e-mails, occasional screenshots and entries in shared Sheets are stitched together when needed. This reactive process is time-consuming and unreliable, making it hard to resolve disputes quickly or to provide audit-grade records. A structured capture mechanism that attaches minimal metadata (who, when, what) to approvals would significantly reduce resolution time.
7. What is your view on balancing quick fixes (SaaS) versus developing custom systems?
Answer: I favour starting with SaaS where it buys speed, lowers upfront cost, and reduces immediate pain. If a SaaS pilot proves the business case and data ownership or auditability is a concern, we can invest in custom systems for long-term control. The decision depends on the pilot results, costs, and how much control we need over data lifecycle and provenance.
8. How do you prioritise competing requests from clients, delivery, and operations?
Answer: We prioritise by client impact and revenue risk first, then by recurring operational cost (tasks that repeatedly consume staff time), and finally by ease and speed of implementation. This approach protects cashflow and targets reductions in predictable overhead; however, we also keep a small buffer for strategic bets or compliance work.
9. Can you describe any recent incidents where fragmented communication or data issues caused a material problem?
Answer: One recent example involved a short WhatsApp message from a client that was interpreted as approval, but because it wasn't linked to the tracked requirement the PM and developer implemented a different set of expectations. The result was a scope mismatch, a delayed invoice and a time-consuming reconciliation involving three teams. That incident highlighted how informal approvals cause downstream rework and client friction.
10. What outcomes would make a project like this successful from your perspective?
Answer: Success would include a measurable reduction in reconciliation and dispute resolution time, consistent capture of approvals linked to work items during pilots, demonstrable freed-up PM capacity, and positive qualitative feedback from staff and at least one client who participated in the pilot. I’d also want clear, objective dashboards showing capture rates, error rates, and operator queue health to make a confident go/no-go decision.
11. How should project-level success metrics map back to leadership KPIs and compensation?
Answer: We should define success metrics that are both operationally meaningful and visible at the leadership level so they can influence prioritisation and resource allocation. Concrete measures might include reduction in hours spent on reconciliation per month, percentage of approvals captured in the canonical system, decrease in the number and duration of billing disputes, and an improvement in on-time delivery rates for pilot teams. These metrics should be reported on a regular cadence and tied into leadership dashboards; where appropriate, they can inform bonuses or recognition for teams that adopt the workflows and demonstrate measurable gains. Importantly, metrics must be resilient to gaming — use a combination of automated capture rates and sampled qualitative audits rather than single-source figures, and ensure that short-term incentives don't encourage cutting corners on data quality or client communication.
12. Are there legal, client, or regulatory constraints around data residency, retention and access that the solution must respect?
Answer: Yes — we have clients in multiple jurisdictions and a mix of contractual obligations that affect how long records must be kept and who can access them. Any design must respect contractual retention windows, the need to pseudonymise or redact sensitive information before keeping long-term records, and the right-to-be-forgotten requirements where applicable. We also need to be able to produce audit trails for billing disputes or compliance checks, so immutable or versioned logs with provenance metadata are important. When considering managed services, ensure they offer clear export and deletion guarantees, and map any third-party storage locations to our legal obligations before proceeding with a pilot.
13. How do you expect change management and training to be handled to ensure staff adopt new workflows?
Answer: Change management should be built into the pilot; it cannot be an afterthought. I expect a small cohort-based rollout where a handful of teams use the new confirmation and ingestion flows while we run frequent check-ins, gather feedback and iterate on UX and exception handling. Champions within each team must be identified to act as first-line support and to encourage peers. Training should be concise and role-specific — a short demo, one-page cheat-sheets, and a few short videos addressing common edge cases — and paired with an accessible rollback or manual-override path so staff retain control. Finally, leadership should visibly support the change by prioritising triage of pilot issues and by recognising teams that participate actively.
14. What criteria should we use when selecting SaaS vendors or gateway providers for messaging and integration?
Answer: Vendor selection should prioritise data portability, clear SLAs, security certifications, and the ability to meet practical integration needs such as webhook reliability and template support for channels like WhatsApp. Evaluate whether the vendor allows you to export raw message content and metadata, supports programmatic redaction or tokenisation, and provides sufficient observability into delivery and rate-limit events. Cost and support responsiveness matter, but they come after assurances around data control and auditability for our use case. Also check commercial terms for limits on API usage, template approvals, and costs for scaling beyond pilot volumes; vendors that lock data into proprietary formats or hinder export should be avoided for core canonical workflows.
15. If the pilot demonstrates measurable benefit, what is an acceptable timeline and investment profile for scaling the solution?
Answer: If pilots deliver the expected reduction in reconciliation time and improved client satisfaction, I would expect a phased scaling plan over 3–9 months depending on scope. The first phase (3 months) should expand the integration to additional high-value accounts and harden operator workflows; the second phase (next 3–6 months) should address full onboarding of remaining teams and remove temporary manual workarounds. Budget-wise, I'm open to a modest upfront investment for a focused 3–6 month pilot (covering SSO, minimal engineering effort, and a managed connector) followed by a defined budget for scaling only if KPIs are met. The scaling plan should include contingency for additional engineering and support, a clear ROI timeline, and a prioritised backlog so we avoid building features that don't materially improve the core metrics.

### HR
1. Describe the current onboarding process for new hires. What typically takes the longest?
Answer: We welcome new hires with standard orientation documents and pair them with a mentor who provides practical guidance in the first weeks. The longest items are arranging access across multiple tools and transferring nuanced project context, including client preferences and informal norms; as a result it typically takes two to four weeks for a new hire to feel productive. Mentors invest significant time answering ad hoc questions and clarifying undocumented practices, which slows overall onboarding throughput.
2. How are role responsibilities and handoffs documented and enforced?
Answer: Formal job descriptions exist, but daily handoffs are often captured in managers' notes, meeting updates or informal documents rather than a single authoritative system. Enforcement is chiefly manager-driven and varies by team, which can create inconsistencies and misunderstandings during transitions. A lightweight centralised handoff record and a simple checklist would improve continuity.
3. How is staff workload and capacity tracked today?
Answer: Workload is tracked in spreadsheets and through manager estimates during planning meetings; there is no single live capacity dashboard. Because of that, capacity issues can remain hidden until they cause delays and require reactive reallocation. Implementing a simple capacity view would allow more proactive balancing and reduce last-minute bottlenecks.
4. Are there recurring staffing or skills gaps that affect delivery?
Answer: Yes — we often see gaps in specialist skills and slower ramping for junior staff due to inconsistent onboarding depth and the lack of a maintained skills inventory. When demand spikes we rely on temporary reassignments, which disrupts planned work. A basic skills registry and periodic upskilling sessions would mitigate this.
5. What HR policies govern access to client data and communications?
Answer: We rely on contractual confidentiality clauses and standard account permissions provided by each tool. We lack company-wide automated controls over chat history and shared documents, which increases exposure risk for sensitive information. Strengthening role-based access and retention policies would reduce this vulnerability.
6. How do you collect feedback from staff about tools and processes?
Answer: Feedback is collected via occasional surveys and through line managers during one-on-ones. Response rates and follow-through can be inconsistent, which makes it hard to prioritise and act on feedback. A continuous lightweight feedback channel with tracked follow-up would improve responsiveness.
7. What training or knowledge-transfer activities exist to reduce single-person dependencies?
Answer: We rely on buddy systems and ad-hoc recorded sessions for knowledge sharing, but we do not currently run a formal curriculum or scheduled cross-training. Consequently, important knowledge can remain concentrated in a few individuals. Introducing structured documentation sprints and a rotation schedule would help spread expertise.
8. How would improved process automation change HR workload or training needs?
Answer: Automation could remove routine administrative tasks such as account provisioning and recurring compliance checks, freeing HR and mentors to focus on coaching and development. However, we would need to invest in initial training and change-management activities to ensure that staff adopt new tools and understand updated workflows.
9. How is employee performance measured relative to process adherence?
Answer: Performance assessments focus mainly on delivery KPIs and manager evaluations; process adherence is observed informally rather than being quantitatively tracked. This means that consistently following process is not always directly rewarded. Introducing a small set of measurable process indicators could help align behaviour with desired practices.
10. What concerns would you have about introducing new tools that change daily workflows?
Answer: Key concerns are adoption friction, a temporary spike in support requests, and the potential for privacy or access-control lapses if tools are not configured correctly. Clear rollout plans, short training sessions, and role-based access rules would help mitigate these issues.
11. What retention challenges do you observe and how do they relate to process pain points?
Answer: Retention challenges often stem from repetitive administrative workloads and unclear career progression for junior staff. When staff feel stuck in low-value tasks without development opportunities, they are more likely to look elsewhere. Reducing manual work and clarifying growth paths would help retention.
12. How well does the current performance review process identify training needs?
Answer: Reviews are periodic but tend to emphasise delivery outcomes rather than explicit skill gaps, making it harder to plan proactive training. A competency-based review framework would better surface development needs and help plan targeted training interventions.
13. How are remote and hybrid work arrangements handled from a policy perspective?
Answer: Remote work is permitted but policies are informal and vary across teams, leading to inconsistent expectations around availability and communication. Defining core hours, expected response times and equipment provisioning would increase predictability for client-facing work.
14. What succession planning exists for critical roles?
Answer: Succession planning is limited and largely informal; critical responsibilities are often known but not comprehensively documented. Establishing documented alternates and cross-training critical functions would reduce the risk of disruption when key staff are unavailable.
15. How would you prioritise HR initiatives if given a modest budget for improvements?
Answer: I would prioritise building a basic skills inventory and a structured onboarding checklist to reduce time-to-productivity, followed by lightweight automation for administrative tasks. Investing in mentor training and a small documentation backlog would deliver meaningful improvements quickly.

### Engineering Manager
1. How is the current development and deployment workflow organised?
Answer: Our current workflow uses feature branches in GitHub with CI/CD orchestrated through GitHub Actions, separate staging and production environments, and manual gates for significant releases. Developers open PRs and request reviews, and releases include a brief verification step by QA or the PM to ensure migrations and release notes are correct. This balance works for our team size but relies on human checks for some safety-critical steps.
2. What are the main pain points in integrating third-party tools (Sheets, WhatsApp, GitHub)?
Answer: Primary pain points include inconsistent or missing identifiers in Sheets, schema drift, WhatsApp template and rate constraints, and uneven webhook support from certain providers. These issues make connectors brittle and require ongoing data cleaning and exception handling. Building resilient connectors requires investment in retries, deduplication logic and operator workflows to handle edge cases.
3. How do you manage schema or API changes for external services?
Answer: We cope with changes via informal contract tests, close cross-team coordination and occasional emergency fixes. There is no formal schema registry or automated change detection, so breaking changes sometimes surface in production. A lightweight contract-testing framework and versioned connector interfaces would reduce these incidents.
4. Describe the current approach to logging, monitoring and incident response.
Answer: We aggregate application logs, but monitoring is fragmented and alerting is configured in several places. Incident response is coordinated over chat and handled ad hoc; this is manageable for smaller incidents but scales poorly for complex outages that span multiple systems. Clear runbooks, centralised alerting and post-incident reviews would improve resilience.
5. What testing strategies are in place for integration points (unit, integration, contract tests)?
Answer: Unit testing is mature, but integration and contract tests are less consistent and typically created per-connector as needed. For higher-confidence integrations we add mock endpoints and reconciliation test cases, but a standardised pipeline for integration testing would increase reliability.
6. How do you prioritise engineering work against operational support tasks?
Answer: Production incidents and urgent support tickets take precedence; planned integration work is scheduled into sprints based on business value and available capacity. We try to reserve a portion of velocity for technical debt and platform improvements to avoid long-term accumulation of operational fragility.
7. What infrastructure or platform constraints (hosting, secret management) should we consider?
Answer: We have limited staging environments, secrets are managed in a simple vault or via environment variables, and budget constraints affect our choice between managed and self-hosted services. These constraints inform decisions about how much to invest in ephemeral testing infrastructure or managed middleware.
8. How would you evaluate an integration platform (self-hosted vs managed)?
Answer: A managed platform is attractive if it reduces maintenance, provides robust retry/observability, and offers SLA-backed support; however, it must also allow data export and provenance controls. If a managed service cannot meet data control or redaction requirements, a self-hosted solution may be warranted despite higher operational cost.
9. What are typical SLAs you can support for synchronization and reconciliation jobs?
Answer: For pilots we can support hourly bulk synchronisations reliably. Near-real-time syncing is feasible for small volumes but requires careful monitoring and rate-limit handling. Tight SLAs for high-volume real-time processing would require additional investment in infrastructure and observability.
10. What data privacy and redaction controls are feasible within current tooling?
Answer: We can implement redaction at ingestion and enforce role-based access in the canonical store; however, some third-party platforms may restrict how redaction can be applied downstream. The recommended approach is to perform redaction before persisting to external systems and to maintain detailed audit logs for access.
11. How do you manage technical debt and prioritise refactoring work?
Answer: Technical debt is tracked in the backlog and usually tackled when it impacts delivery or stability; we don't have a systematic cadence for refactoring. Allocating a regular percentage of sprint capacity for debt reduction would help maintain velocity and reduce long-term support costs.
12. What metrics do you use to assess integration health?
Answer: Key metrics include sync success rate, reconciliation discrepancy counts, mean time to detect and resolve errors, queue depth, and operator backlog age. Tracking these metrics over time helps prioritise improvements and detect regressions early.
13. What is your approach to secure credential management for integrations?
Answer: Credentials are stored in a secrets vault or environment variables with limited access; rotation is manual in many cases. Automating credential rotation and integrating secrets with the deployment pipeline would reduce exposure risk and administrative overhead.
14. How do you plan capacity for peak loads or bursts?
Answer: We prefer batching and throttling strategies with backpressure handling rather than attempting to scale for unbounded real-time throughput. For anticipated large bursts we schedule bulk sync windows and, if necessary, provision temporary resources to handle the load.
15. What would you like to see improved in the developer experience to help integrations succeed?
Answer: Better sandbox or mock endpoints for external services, a lightweight schema registry, reusable connector templates, and clearer contract-testing tooling would improve development speed and reduce surprises in production. Improved documentation and example mappings for common sheets formats would also help reduce onboarding time for new connectors.

### Employees (Delivery / PM / Ops)
1. Describe a typical day and the tools you use most frequently.
Answer: A typical day involves frequent context switching between WhatsApp/Slack for quick messages, Google Sheets for trackers, GitHub for code and issue management, and our task tracker for assignments. Much of the day is spent clarifying small points, updating trackers and responding to client or internal queries, which creates cognitive load and frequent interruptions. These transitions make it difficult to maintain deep focus and increase the time required to complete higher-value tasks.
2. How do you capture decisions, approvals and changes to scope?
Answer: Most decisions and approvals are captured informally in chat; only when a dispute or billing need is anticipated do we add formal notes to Sheets or ticket comments. This reactive capture process often results in incomplete records that are hard to audit later. A lightweight confirmation workflow that attaches metadata to an approval would improve traceability.
3. Which tasks require repeated manual work or copy-paste between tools?
Answer: Repetitive tasks include copying client messages into Sheets, updating statuses in multiple systems, and reconciling billing notes. These manual steps take time and are prone to mistakes, diverting effort from client communication and quality assurance.
4. What problems do you face when tracking task ownership or deadlines?
Answer: Ownership gets blurred when several people contribute to a thread, and fragmented context leads to missed deadlines because not everyone shares the same understanding of the task. Having a single authoritative owner field linked to the approval or task would reduce confusion and improve accountability.
5. How often do you need to ask colleagues to clarify prior messages or decisions?
Answer: I typically need to ask for clarifications multiple times per week, especially when approvals were informal or lacked key details. These clarifications interrupt workflows and can compound delays as items pile up.
6. What would make your daily work noticeably easier?
Answer: A one-click confirmation flow that links approvals to the related task, clearer templates for client requests, and fewer overlapping tools would make daily work noticeably easier and reduce rework. Even small structured messages that capture essential metadata would save time.
7. Are there tools or features you currently avoid because they are too slow or unreliable?
Answer: We avoid heavy CRMs and any tools requiring duplicate entry or manual syncing. Tools that add friction to quick conversational workflows rarely get adopted, even if they offer better structure.
8. Do you keep copies of client messages or important approvals outside of work tools? Why?
Answer: Yes—sometimes I take screenshots or keep local notes because the main tools don't always preserve context in a retrievable way. This helps in dispute scenarios but introduces security and organisational consistency issues.
9. How comfortable are you with small automation that reduces repetitive tasks?
Answer: I'm open to small automations that reduce repetitive work, provided they preserve key context and offer an easy manual override for exceptions. Suggested automations that surface recommended updates rather than auto-applying them would be most acceptable.
10. What would you want to see in training or documentation for new workflows?
Answer: Short, practical how-to guides, quick video demos for common tasks and in-app tips are most effective. Long manuals are rarely read; bite-sized guidance works best for adoption.
11. How easily can you access historical project notes when needed?
Answer: Accessing historical notes is often time-consuming because records are scattered across chat threads, Sheets and ticket comments. Search is imperfect and context can be lost, so reconstructing history frequently requires asking colleagues directly.
12. Who do you contact when you find inconsistent or missing information?
Answer: We escalate to the project manager or account lead, and if necessary, to the person who last updated the tracker. This approach depends heavily on people's availability and can introduce delays.
13. What worries you most about partial automation of tasks you currently perform manually?
Answer: I worry automation might misclassify messages or strip important context, leading to incorrect updates that are hard to detect. Without a clear audit trail and manual override, automation could cause more harm than benefit.
14. Would you be willing to participate in a pilot for a new approval capture workflow?
Answer: Yes—I would participate if the pilot minimizes disruption and includes a rollback plan. I would expect regular check-ins so issues can be addressed quickly.
15. How do you see knowledge-sharing happening informally today?
Answer: Knowledge-sharing happens through quick messages, recorded calls and shadowing, but it's inconsistent and not always archived properly. Creating short, searchable notes from key sessions would make knowledge propagation more reliable.

### Customers
1. How do you prefer to communicate with our team (chat, email, calls)?
Answer: I prefer WhatsApp or chat for quick clarifications and short questions, and e-mail for formal confirmations or anything that might affect invoicing or scope. For more complex discussions I am open to scheduled calls, but agreeing up front on a single channel for confirmations reduces ambiguity and speeds decisions.
2. Do you feel confident that your approvals and confirmations are recorded accurately?
Answer: Not always. While I assume the provider captures approvals, the lack of an explicit confirmation mechanism creates uncertainty; I'd feel more confident with a clear, single-step confirmation tied to the task or change.
3. Have you experienced delays or repeated questions from the team due to unclear instructions?
Answer: Occasionally — follow-up questions arise when instructions are incomplete or when staff interpret context differently. These small delays add up and can be avoided with clearer templates or a short confirmation workflow.
4. How important is it for you that approvals are traceable for billing or contract reasons?
Answer: Very important. Traceable approvals are essential for billing clarity and for resolving disputes efficiently. When approvals are time-stamped and linked to a task, reconciliation is straightforward.
5. What is the simplest way we could make communication easier for you?
Answer: A short confirmation message or an in-app button that records the approval would make it much easier and reduce the need for follow-ups. If that confirmation were also included in the invoice or a weekly summary, it would streamline billing conversations.
6. Would you be comfortable using a brief in-app confirmation workflow if it saved time?
Answer: Yes — I would use a quick in-app confirmation if it's low-friction and doesn't add extra steps to my normal routine. Anything that reduces follow-ups and speeds resolution is welcome.
7. How much documentation would you expect attached to an approval (e.g., scope note, screenshots)?
Answer: For minor approvals a short scope note suffices; for larger changes I expect a brief description of impact on timeline and cost, plus any relevant screenshots. Keeping documentation concise but sufficient is important.
8. Have you ever disputed an invoice due to unclear approvals? What happened?
Answer: Yes—once a billing dispute arose because a scope change was implemented without a clear, linked approval. It required sharing chat logs and emails to resolve and took several days. A recorded approval would have resolved it quicker.
9. How do you prefer to receive project summaries or release notes?
Answer: I prefer short weekly summaries via email with links to any supporting messages or tickets. Highlighting decisions and open actions at the top makes it easier to scan.
10. What would make you more confident in the company's record-keeping around approvals?
Answer: Automatic linking of approvals to the relevant ticket, a visible audit trail showing who approved and when, and easy export options for records would increase confidence. Simple access controls and clear retention policies would also help.
11. How do you expect disputes to be handled, and what turnaround time is acceptable?
Answer: I expect disputes to be acknowledged within two business days and resolved within a week for routine matters. Faster acknowledgement demonstrates attention and reduces escalation.
12. Are you concerned about how your messages are stored or who can access them?
Answer: Somewhat — I expect providers to limit access to necessary staff and to redact sensitive content when appropriate. Clear policies on retention and deletion would reassure me.
13. Would you participate in a pilot that changes how approvals are captured if it reduced billing errors?
Answer: Yes — I would participate if the pilot is low-friction and demonstrably reduces billing issues. Being part of the pilot would let me feed back on the UX and ensure it meets client needs.
14. How would you like to be informed when a change affects timeline or cost?
Answer: I would like an immediate notification via the agreed channel summarising the impact on timeline and cost, followed by an updated plan or invoice if required. Clear, concise communication reduces uncertainty and supports planning.
15. What trust signals would you expect before sharing sensitive information in chat?
Answer: I would expect a clear privacy policy, limited access controls, evidence of secure storage and redaction capabilities, and the option to mark messages as sensitive. Knowing there is an auditable approval mechanism and that data access is logged would increase trust.

---

## Questionnaires

This section contains closed-question surveys for each stakeholder group. Open-ended prompts have been removed. Use Likert scale 1–5 (1 = Strongly disagree / Never, 5 = Strongly agree / Always) unless otherwise stated.

### CEO Questionnaire (Likert 1–5)
- Q1: The company has clear, consistently-applied processes for capturing client approvals.
- Q2: Current tools give leadership a reliable view of project status.
- Q3: Operational errors (billing, scope drift) are primarily caused by process gaps rather than resourcing.
- Q4: The company can afford short-term SaaS subscriptions to solve urgent problems.
- Q5: Data provenance and auditability are high priorities for the company.
- Q6: Improvements in integrations would significantly reduce operational overhead.
- Q7: I am willing to allocate budget to a validated pilot that reduces manual reconciliation.

### HR Questionnaire (Likert 1–5)
- Q1: New hires reach baseline productivity within two months.
- Q2: Role responsibilities are clearly documented and accessible.
- Q3: We have reliable data on individual and team capacity.
- Q4: There is sufficient internal training to support new tools.
- Q5: Skills and competencies are regularly updated in a central place.
- Q6: HR receives frequent requests to clarify task ownership.
- Q7: Automation would free enough staff time to justify its cost.
- Q8: Access to client communications is managed appropriately for privacy.
- Q9: We have an effective mentor program for junior staff.
- Q10: Staff are generally open to small process changes that reduce repetitive work.

### Engineering Manager Questionnaire (Likert 1–5)
- Q1: Our engineering team can support a small integration pilot within existing capacity.
- Q2: We have sufficient testing environments for integration validation.
- Q3: The current logging and monitoring practices are adequate for production use.
- Q4: We can implement redaction and access controls without major platform changes.
- Q5: Managed iPaaS solutions would reduce engineering effort compared to building connectors in-house.
- Q6: We have clear procedures for rolling back migrations or syncs.
- Q7: Integration work is easier when canonical IDs are available across systems.
- Q8: Rate limits on external APIs are a significant constraint for planned integrations.
- Q9: We have an established process for maintaining connector code and tests.
- Q10: Observability tools are available to track end-to-end integration health.

### Employees Questionnaire (Likert 1–5)
- Q1: I can find the latest version of a client instruction without asking a colleague.
- Q2: I often spend time reconciling information between tools.
- Q3: Approvals given in chat are usually sufficient for me to proceed.
- Q4: I regularly need to redact or remove sensitive client information before saving it.
- Q5: Automated assignment would reduce my time on routine tasks.
- Q6: I have clear guidance on which channel to use for formal approvals.
- Q7: I am confident that the tools we use maintain accurate records for billing.
- Q8: I sometimes save client messages locally for my reference.
- Q9: I would use a one-click confirmation flow if it were available.
- Q10: I receive too many notifications from tools.
- Q11: I can access historical project notes easily.
- Q12: I know who to contact when a data inconsistency is found.
- Q13: I feel the current workflows support timely delivery.
- Q14: I have adequate time for impromptu clarifications that arise during a project.
- Q15: I am willing to try small workflow changes if they reduce manual work.

Frequency items (Never / Rarely / Sometimes / Often / Always)
- F1: How often do you copy data between tools?
- F2: How often do you need to escalate a clarification to a manager?

### Customer Questionnaire (Likert 1–5)
- Q1: I am satisfied with the clarity of communication from Nextstepbd.
- Q2: I can easily confirm scope changes when requested.
- Q3: I have experienced billing issues caused by miscommunication.
- Q4: I would prefer a formal confirmation button for approvals rather than informal messages.
- Q5: I find it easy to retrieve past messages or confirmations when needed.
- Q6: Response times to my queries are acceptable.
- Q7: I trust the company to handle my data appropriately.
- Q8: I would be willing to use a brief in-app confirmation step if it saves clarification time.
- Q9: I have needed the company to produce evidence of approval for billing or audit purposes.
- Q10: Overall, I am satisfied with project delivery.

---

## Rubrics and Scoring Guidance

General Likert interpretation (per-item)
- 1 (Strongly disagree / Never): Clear problem or strong negative signal.
- 2 (Disagree / Rarely): Concerning; likely needs targeted action.
- 3 (Neutral / Sometimes): Mixed; investigate with follow-ups or qualitative interviews.
- 4 (Agree / Often): Positive signal; may still have isolated issues.
- 5 (Strongly agree / Always): Strong positive signal; generally healthy in this area.

Suggested aggregate thresholds (per questionnaire)
- Average <= 2.5: High priority — plan immediate remedial actions and detailed follow-up interviews.
- Average > 2.5 and < 3.5: Medium priority — investigate specific low-scoring items and validate with interviews.
- Average >= 3.5: Low priority — maintain and monitor; consider pilot for incremental improvement.

Per-role interpretive notes
- CEO: Low scores on Q1–Q3 indicate gaps in governance and visibility; low Q7 suggests budget resistance.
- HR: Low scores on Q1–Q4 indicate onboarding and training weaknesses; prioritize mentor programs and documentation.
- Engineering Manager: Low scores on Q1–Q3 or Q10 indicate capacity or observability gaps; consider managed services or more testing infra.
- Employees: Low scores on Q1–Q5 indicate operational pain points and manual work; target connector pilots and operator flows.
- Customers: Low scores on Q1–Q6 indicate customer-experience issues; prioritise communication clarity and confirmation workflows.

Using the rubrics
- Compute per-question averages and overall questionnaire average.
- Highlight items with average <= 3 for qualitative follow-up.
- Combine questionnaire findings with interview themes to produce recommendations.

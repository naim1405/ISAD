# Interview Questions & Questionnaires

This file provides two sections: (1) Interview Questions — open, role-specific prompts for semi-structured interviews; and (2) Questionnaires — closed items for survey distribution.

---

## Interview Questions

### CEO
1. Can you describe the company's current strategic priorities for the next 12–24 months?
Answer: Over the next year or two we want to focus on growing revenue from our existing client base while improving how reliably we deliver projects. Practically, that means investing in processes and tools that reduce manual rework, improving predictability so clients receive work on time, and piloting automation to free up project managers. We're also exploring one or two productised services to create steadier recurring income.
2. What are the most important operational risks you see today?
Answer: The biggest risks I worry about are information getting lost in conversations, which then causes scope confusion or billing errors; having single people who are the only holders of certain knowledge; and security exposure from using informal channels for client details. Any of these can impact cashflow or client trust if left unaddressed.
3. How do you measure service delivery success and client satisfaction?
Answer: We look at on-time delivery and client satisfaction checks after engagements. We also track billing disputes and the time PMs spend resolving issues — reductions in those are strong indicators of improved delivery and clarity.
4. Which processes or tools do you think limit the company's ability to scale?
Answer: Relying on spreadsheets and chat for critical approvals limits our ability to scale. Without canonical identifiers for clients or contracts and without structured confirmations, we end up hiring more people just to maintain consistency.
5. How are decisions about investment in tools, integrations, and people made?
Answer: We balance ROI and time-to-value. For urgent pain points we favour low-friction SaaS pilots; for long-term capability or compliance needs we consider custom work. Larger expenditures require sponsor approval and a clear business case.
6. How do you currently obtain evidence for client approvals, scope changes, or billing disputes?
Answer: Most evidence today is patched together from chat threads, emails, occasional screenshots and entries in Sheets. That reactive approach is error-prone and inefficient when we need to prove what was agreed.
7. What is your view on balancing quick fixes (SaaS) versus developing custom systems?
Answer: I favour starting with SaaS when it buys speed and reduces immediate pain. If a pilot proves valuable or data ownership and auditability demand it, we will consider investing in custom systems.
8. How do you prioritise competing requests from clients, delivery, and operations?
Answer: We prioritise by client impact and revenue risk first, then by recurring manual effort that drives cost, and finally by ease and speed of implementation. This helps protect cashflow and reduce predictable overhead.
9. Can you describe any recent incidents where fragmented communication or data issues caused a material problem?
Answer: Recently a client’s informal approval was buried in a long chat and caused a scope mismatch that delayed invoicing. It required several people across teams to piece together the evidence, costing time and putting strain on the client relationship.
10. What outcomes would make a project like this successful from your perspective?
Answer: Success would look like a measurable drop in reconciliation and dispute resolution time, consistent traceable approval records in pilots, freed-up PM capacity, and positive feedback from pilot teams and at least one client participant.

### HR
1. Describe the current onboarding process for new hires. What typically takes the longest?
Answer: We provide welcome documents and pair new hires with a mentor. The longest parts are arranging tool access and transferring project-specific context; as a result it usually takes two to four weeks for a new hire to feel productive and confident in their role.
2. How are role responsibilities and handoffs documented and enforced?
Answer: Formal job descriptions exist, but day-to-day handoffs are usually recorded in managers' notes or informal documents. Enforcement is largely manager-driven rather than centrally enforced, which can create inconsistencies across teams.
3. How is staff workload and capacity tracked today?
Answer: We rely on spreadsheets and manager estimates to track workload and capacity. Because there is no unified live dashboard, capacity issues can go unnoticed until they become urgent and require reactive rebalancing.
4. Are there recurring staffing or skills gaps that affect delivery?
Answer: Yes — onboarding depth for junior staff and the absence of a maintained skills inventory mean we sometimes lack specialists when demand spikes. This leads to temporary reassignments and occasional delivery delays.
5. What HR policies govern access to client data and communications?
Answer: We rely on confidentiality clauses in contracts and standard account permissions for tools. We do not yet have automated company-wide controls for chat history or shared documents, which increases risk around sensitive client data.
6. How do you collect feedback from staff about tools and processes?
Answer: Feedback is gathered through occasional surveys and manager channels. Response rates and follow-through vary, so it is difficult to prioritise and act on staff suggestions consistently.
7. What training or knowledge-transfer activities exist to reduce single-person dependencies?
Answer: We use buddy systems and occasionally record knowledge-transfer sessions, but we lack a formal curriculum or regular cross-training schedule. That means some critical knowledge remains concentrated in individuals.
8. How would improved process automation change HR workload or training needs?
Answer: Improved automation would reduce repetitive administrative tasks and free mentors for coaching and skill development. However, it would require upfront training and change management to ensure consistent adoption and to update onboarding materials.
9. How is employee performance measured relative to process adherence?
Answer: Performance is measured primarily through delivery KPIs and manager assessments. Process adherence is noted informally rather than captured in quantitative metrics, so it doesn't directly influence performance reviews.
10. What concerns would you have about introducing new tools that change daily workflows?
Answer: My main concerns are adoption friction and a short-term spike in support requests as people learn new workflows. I would also want clear assurances that client privacy is preserved when integrating new tools.

### Engineering Manager
1. How is the current development and deployment workflow organised?
Answer: Our development workflow uses GitHub feature branches and CI via GitHub Actions, with separate staging and production environments. For major releases we keep manual deployment gates so engineers can perform final checks before going live.
2. What are the main pain points in integrating third-party tools (Sheets, WhatsApp, GitHub)?
Answer: The main pain points are inconsistent or missing identifiers in Sheets, changing schemas, WhatsApp API template and rate constraints, and limited webhook support from some providers. These issues make reliable synchronization and error handling more difficult.
3. How do you manage schema or API changes for external services?
Answer: We handle schema and API changes with informal contract tests and close coordination between teams. We don't yet have a formal schema registry or automated change-management process, which can slow down responses to breaking changes.
4. Describe the current approach to logging, monitoring and incident response.
Answer: We collect application logs but our monitoring is fragmented and alerting is inconsistent. Incident response is typically coordinated over chat and tends to be largely informal, which works for smaller incidents but would not scale well for complex outages.
5. What testing strategies are in place for integration points (unit, integration, contract tests)?
Answer: Unit testing is well established, but integration and contract tests are limited and usually added on a per-connector basis when time permits. For higher-confidence integrations we'd like more systematic integration testing.
6. How do you prioritise engineering work against operational support tasks?
Answer: Production incidents and urgent support requests take precedence. Integration and platform improvements are prioritized into sprints according to business value and team capacity.
7. What infrastructure or platform constraints (hosting, secret management) should we consider?
Answer: We have limited staging capacity, secrets are stored in a simple vault or environment variables, and budget constraints affect our ability to adopt managed services. These constraints influence choices around testing and platform selection.
8. How would you evaluate an integration platform (self-hosted vs managed)?
Answer: I would prefer a managed integration platform if it reduces maintenance workload and provides robust retry and observability features. However, it must support strong provenance and data control; otherwise we would consider a self-hosted approach.
9. What are typical SLAs you can support for synchronization and reconciliation jobs?
Answer: For pilot projects we can comfortably support hourly bulk synchronizations. Near-real-time syncing is feasible for lower volumes, but it requires careful monitoring and handling of rate limits and backpressure.
10. What data privacy and redaction controls are feasible within current tooling?
Answer: We can implement redaction at the ingestion layer and enforce role-based access in a canonical store. Third-party platforms may limit how strictly we can enforce redaction, so the architecture should be designed to mitigate those limitations.

### Employees (Delivery / PM / Ops)
1. Describe a typical day and the tools you use most frequently.
Answer: A typical day involves frequent context switching between WhatsApp or Slack for quick messages, Google Sheets for trackers, GitHub for code-related tasks, and our task tracker. We also spend time in short meetings and impromptu clarifications to keep projects moving.
2. How do you capture decisions, approvals and changes to scope?
Answer: Most decisions and approvals are captured in chat, and formal notes are only added to Sheets or task comments later when it's convenient or if we expect the decision will need to be referenced.
3. Which tasks require repeated manual work or copy-paste between tools?
Answer: Repetitive tasks include copying client messages into Sheets, updating ticket statuses across multiple tools, and reconciling billing notes—activities that are time-consuming and error-prone.
4. What problems do you face when tracking task ownership or deadlines?
Answer: Ownership becomes unclear when multiple people contribute to a thread, and fragmented context can lead to missed deadlines because not everyone has the same understanding of the task.
5. How often do you need to ask colleagues to clarify prior messages or decisions?
Answer: I typically need to ask colleagues for clarification several times per week, especially when approvals were informal or lacked important details.
6. What would make your daily work noticeably easier?
Answer: A lightweight confirmation flow for approvals, clearer request templates, and reducing overlapping tools would make daily work noticeably easier and reduce rework.
7. Are there tools or features you currently avoid because they are too slow or unreliable?
Answer: We tend to avoid heavy CRMs and any tools that force duplicate entry or manual syncing because they slow us down and add friction.
8. Do you keep copies of client messages or important approvals outside of work tools? Why?
Answer: Yes, sometimes I keep screenshots or local notes for quick reference or as billing evidence when I don't trust that the primary tools will preserve context in a retrievable way.
9. How comfortable are you with small automation that reduces repetitive tasks?
Answer: I'm generally positive about small automations that reduce repetitive tasks, provided they preserve context and include an easy manual override when needed.
10. What would you want to see in training or documentation for new workflows?
Answer: Short, practical how-to guides with examples and in-app tips would help adoption far more than long formal training modules.

### Customers
1. How do you prefer to communicate with our team (chat, email, calls)?
Answer: I prefer WhatsApp or chat for quick exchanges and email for formal confirmations. It's helpful when we agree on a single preferred channel for each engagement to avoid confusion.
2. Do you feel confident that your approvals and confirmations are recorded accurately?
Answer: Not always — I often assume approvals are tracked, but I would feel more confident with explicit confirmation steps that clearly record approvals for both parties.
3. Have you experienced delays or repeated questions from the team due to unclear instructions?
Answer: Occasionally — follow-up questions sometimes arise from unclear instructions, which can cause small delays in delivery.
4. How important is it for you that approvals are traceable for billing or contract reasons?
Answer: Very important — traceable approvals are essential for billing clarity and for resolving any contract disputes that may occur.
5. What is the simplest way we could make communication easier for you?
Answer: A short confirmation message or an in-app button that explicitly records approvals would be the simplest and most useful improvement to communication.

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

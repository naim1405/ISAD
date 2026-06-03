# Interview Questions & Questionnaires

This file provides two sections: (1) Interview Questions — open, role-specific prompts for semi-structured interviews; and (2) Questionnaires — closed items for survey distribution.

---

## Interview Questions

### CEO
1. Can you describe the company's current strategic priorities for the next 12–24 months?
2. What are the most important operational risks you see today?
3. How do you measure service delivery success and client satisfaction?
4. Which processes or tools do you think limit the company's ability to scale?
5. How are decisions about investment in tools, integrations, and people made?
6. How do you currently obtain evidence for client approvals, scope changes, or billing disputes?
7. What is your view on balancing quick fixes (SaaS) versus developing custom systems?
8. How do you prioritise competing requests from clients, delivery, and operations?
9. Can you describe any recent incidents where fragmented communication or data issues caused a material problem?
10. What outcomes would make a project like this successful from your perspective?

### HR
1. Describe the current onboarding process for new hires. What typically takes the longest?
2. How are role responsibilities and handoffs documented and enforced?
3. How is staff workload and capacity tracked today?
4. Are there recurring staffing or skills gaps that affect delivery?
5. What HR policies govern access to client data and communications?
6. How do you collect feedback from staff about tools and processes?
7. What training or knowledge-transfer activities exist to reduce single-person dependencies?
8. How would improved process automation change HR workload or training needs?
9. How is employee performance measured relative to process adherence?
10. What concerns would you have about introducing new tools that change daily workflows?

### Engineering Manager
1. How is the current development and deployment workflow organised?
2. What are the main pain points in integrating third-party tools (Sheets, WhatsApp, GitHub)?
3. How do you manage schema or API changes for external services?
4. Describe the current approach to logging, monitoring and incident response.
5. What testing strategies are in place for integration points (unit, integration, contract tests)?
6. How do you prioritise engineering work against operational support tasks?
7. What infrastructure or platform constraints (hosting, secret management) should we consider?
8. How would you evaluate an integration platform (self-hosted vs managed)?
9. What are typical SLAs you can support for synchronization and reconciliation jobs?
10. What data privacy and redaction controls are feasible within current tooling?

### Employees (Delivery / PM / Ops)
1. Describe a typical day and the tools you use most frequently.
2. How do you capture decisions, approvals and changes to scope?
3. Which tasks require repeated manual work or copy-paste between tools?
4. What problems do you face when tracking task ownership or deadlines?
5. How often do you need to ask colleagues to clarify prior messages or decisions?
6. What would make your daily work noticeably easier?
7. Are there tools or features you currently avoid because they are too slow or unreliable?
8. Do you keep copies of client messages or important approvals outside of work tools? Why?
9. How comfortable are you with small automation that reduces repetitive tasks?
10. What would you want to see in training or documentation for new workflows?

### Customers
1. How do you prefer to communicate with our team (chat, email, calls)?
2. Do you feel confident that your approvals and confirmations are recorded accurately?
3. Have you experienced delays or repeated questions from the team due to unclear instructions?
4. How important is it for you that approvals are traceable for billing or contract reasons?
5. What is the simplest way we could make communication easier for you?

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
- Q14: I have adequate time for ad-hoc clarifications that arise during a project.
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

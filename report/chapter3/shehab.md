
# Planning Introduction

Project planning is a structured management process that establishes the objectives, scope, schedule, resources, cost framework, communication structure, and quality expectations required for successful project execution. Effective planning provides a roadmap that guides the project team from initiation through deployment while ensuring that organisational goals, stakeholder expectations, and operational constraints remain aligned throughout the project lifecycle.

For technology integration initiatives, project planning is particularly important because such projects involve multiple interdependent activities, technical uncertainties, resource limitations, and cross-functional stakeholder coordination. A well-defined planning process helps organisations minimise implementation risk, control project expenditure, manage schedule performance, allocate responsibilities clearly, and establish measurable quality standards before execution begins.

Project planning is generally performed through a series of interconnected management activities. These activities include defining project scope, identifying stakeholders, estimating activity durations and costs, sequencing implementation tasks, establishing communication procedures, developing risk responses, and defining quality assurance mechanisms. Together, these planning activities create a structured baseline against which project performance can later be monitored and controlled.

In the context of the Integrated Agency Management System (IAMS) project at NextStepBD, planning was especially important because the project involved the integration of multiple enterprise platforms, organisational workflow transformation, and coordination between management, project teams, developers, and external clients. Since the project aimed to replace fragmented operational practices with a centralized integration ecosystem, careful planning was required to ensure minimal operational disruption while maintaining service continuity during implementation.

The planning process for IAMS evolved through three major stages: the initial proposed plan, stakeholder discussion and evaluation, and the revised implementation plan. This iterative planning approach ensured that the final project strategy aligned with both the technical realities of the organisation and the business expectations of key stakeholders.

---

## Initial Proposed Plan

The initial project proposal focused on developing a custom-built internal management system that would centralize client communication, project management, task tracking, reporting, and developer coordination into a single proprietary platform. The early concept included the development of a dedicated database, a custom user interface, automated task assignment logic, and internal reporting dashboards.

At this stage, the project was approached as a traditional software development initiative. Preliminary planning assumed that the organisation would design and build most system components internally using its own development team. The proposed plan also included custom workflow automation, direct client interaction modules, and internally managed infrastructure.

Although the initial proposal appeared technically feasible, early analysis identified several major concerns relating to development cost, implementation duration, opportunity cost of developer time, and long-term maintenance overhead.

### Figure 3.1: Evolution of the IAMS Project Planning Strategy

*[Insert Figure 3.1 here]*

---

## Stakeholder Discussion

To evaluate the practicality of the initial proposal, a formal stakeholder strategy review meeting was conducted on 5 May 2026 involving the CEO, Project Manager, Coding Team Lead, and representatives from the development and operations teams.

During the discussion, several critical issues were raised.

The CEO expressed concern that building a fully custom enterprise platform would consume a large portion of the company’s billable developer hours, significantly increasing operational costs while delaying return on investment. From a business perspective, the proposed development effort was considered too expensive relative to the availability of mature SaaS alternatives already available in the market.

The Project Manager raised concerns regarding workflow governance and communication control. Specifically, allowing clients unrestricted access to developer-level tasks and workflows could create scope creep, unstructured feedback, and operational disruption for the technical team.

The Coding Team Lead also highlighted technical and architectural concerns. The original proposal included automated task assignment mechanisms based primarily on workload metrics; however, the Team Lead argued that such automation could not reliably account for developer specialization, task complexity, or contextual project knowledge. Additionally, the need to design a custom database schema was questioned, given that enterprise platforms such as Jira already provide highly configurable workflow and issue management structures.

These stakeholder discussions fundamentally changed the direction of the project.

---

## Revised Plan

Following stakeholder evaluation, the project strategy was revised from a custom software development initiative into a SaaS-based integration project built around a “Buy over Build” philosophy.

Instead of developing a monolithic internal platform, the revised plan proposed integrating existing enterprise tools including:

* Jira Software
* Jira Service Management (JSM)
* Slack
* GitHub
* ScriptRunner
* Confluence

Under the revised approach, Jira Software was designated as the Single Source of Truth (SSOT) for all project and operational data. Jira Service Management would manage structured client communication and triage workflows, while Slack and GitHub would provide integrated collaboration and development automation.

The revised plan significantly reduced implementation complexity, development effort, project duration, and financial risk. Rather than building core enterprise features from scratch, the project team would focus on:

* Workflow configuration
* API integration
* Webhook automation
* Role-Based Access Control (RBAC) setup
* ETL data migration
* Quality assurance and operational optimisation

This revised strategy also preserved developer productivity by minimizing non-billable internal software development work while still achieving the operational objectives originally envisioned in the initial proposal.

As a result, the final planning framework for IAMS became more practical, cost-efficient, scalable, and aligned with stakeholder expectations.

---

### Table 3.1: Comparison Between Initial Proposed Plan and Revised Integration Plan

*[Insert Table 3.1 here]*

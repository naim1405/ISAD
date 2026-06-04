# 4.3.2 Data Flow Diagram (DFD) of Existing System

Data Flow Diagrams (DFDs) were developed to represent the flow of information within Nextstepbd's current operational environment. The diagrams illustrate how information is created, transferred, stored, and utilized across different stakeholders and systems. The purpose of these DFDs is to identify inefficiencies, duplication of effort, communication gaps, and operational bottlenecks within the existing environment.

The analysis revealed that information frequently moves through multiple disconnected platforms including WhatsApp, Email, Google Sheets, GitHub, and manual records. As a result, critical business information is often duplicated, inconsistently maintained, and difficult to trace. The DFDs presented below visualize these issues and provide the foundation for the improved system proposed in later chapters.

---

# 4.3.2.1 DFD of Whole Existing System (Context Diagram)

## Purpose

The Context DFD provides a high-level view of the entire organization as a single system and illustrates its interactions with external entities.

---

## Context DFD Description

### Process

**P0 – Nextstepbd Existing Information System**

This process represents all operational activities currently performed by the company using a combination of manual procedures and disconnected software tools.

---

### External Entities

#### E1 – Customers

Provide:

* Project inquiries
* Requirements
* Change requests
* Approvals
* Feedback
* Payments

Receive:

* Quotations
* Progress updates
* Deliverables
* Invoices
* Support responses

---

#### E2 – Management (CEO)

Provide:

* Strategic decisions
* Business objectives
* Budget approvals

Receive:

* Project status reports
* Operational reports
* Financial summaries

---

#### E3 – Employees

Provide:

* Development updates
* Task progress
* Technical documentation
* Internal communication

Receive:

* Tasks
* Requirements
* Instructions
* Project assignments

---

#### E4 – HR Department

Provide:

* Employee records
* Performance evaluations
* Attendance information

Receive:

* Employee updates
* Staffing requirements

---

## Data Flows

| Source                      | Data Flow               | Destination                 |
| --------------------------- | ----------------------- | --------------------------- |
| Customer                    | Requirements, Approvals | Existing Information System |
| Existing Information System | Deliverables, Invoices  | Customer                    |
| CEO                         | Policies, Decisions     | Existing Information System |
| Existing Information System | Reports                 | CEO                         |
| Employees                   | Task Updates            | Existing Information System |
| Existing Information System | Tasks, Instructions     | Employees                   |
| HR                          | Employee Information    | Existing Information System |
| Existing Information System | Staffing Requests       | HR                          |

---

## Diagram Specification for Drawing

```text
                    +----------------+
                    |   Customer     |
                    +----------------+
                       |         ^
 Requirements          |         | Deliverables
 Approvals             |         | Invoices
                       v         |
                +----------------------+
                |  P0: Nextstepbd      |
                | Existing Information |
                |      System          |
                +----------------------+
                   ^      ^        ^
                   |      |        |
                   |      |        |
                   |      |        |
        Reports    |      | Tasks  | Staffing
                   |      |         Requests
                   |      |
      +------------+      +-------------+
      |                               |
      v                               v
+------------+                 +------------+
|    CEO     |                 | Employees  |
+------------+                 +------------+
                                     ^
                                     |
                                     |
                                     |
                              +-------------+
                              |     HR      |
                              +-------------+
```

---

# 4.3.2.2 DFD of Key Subsystems Addressing Organizational Issues

Based on the problem analysis conducted in Chapters 1 and 4, two subsystems were identified as the most critical contributors to organizational inefficiency:

1. Communication & Collaboration Subsystem
2. Data Management & Project Tracking Subsystem

---

# A. Communication & Collaboration Subsystem

## Purpose

This subsystem demonstrates how project-related communication currently flows through informal channels and highlights the communication fragmentation problem.

---

## External Entities

* Customer
* Project Manager
* Developer
* QA Engineer

---

## Processes

### P1.1 Receive Client Requirements

Requirements arrive through WhatsApp, Email, and meetings.

### P1.2 Communicate Requirements

Project manager interprets and distributes information to team members.

### P1.3 Execute Development Tasks

Developers perform assigned work.

### P1.4 Validate Deliverables

QA verifies completed work.

### P1.5 Deliver Updates to Customer

Project status and completed work are communicated back to customers.

---

## Data Stores

### D1 – WhatsApp Messages

Contains:

* Approvals
* Clarifications
* Scope changes

Issue:

No structured tracking.

---

### D2 – Email Records

Contains:

* Client correspondence
* Attachments

Issue:

Information scattered across threads.

---

### D3 – Project Notes

Contains:

* Meeting notes
* Internal decisions

Issue:

Not consistently maintained.

---

## Data Flows

Customer → Requirements → P1.1

P1.1 → Requirement Details → P1.2

P1.2 → Tasks → Developer

Developer → Progress Updates → P1.3

P1.3 → Completed Features → P1.4

P1.4 → Approved Deliverables → P1.5

P1.5 → Updates → Customer

P1.1 ↔ D1

P1.1 ↔ D2

P1.2 ↔ D3

---

## Key Problems Visible

* Requirements stored in multiple locations.
* Approvals buried in chats.
* PM becomes communication bottleneck.
* Poor traceability of decisions.

---

# B. Data Management & Project Tracking Subsystem

## Purpose

This subsystem illustrates how operational and project information is maintained across disconnected systems.

---

## External Entities

* Project Manager
* Developer
* Finance Officer
* Management

---

## Processes

### P2.1 Record Project Information

Store client and project information.

### P2.2 Update Task Status

Maintain development progress.

### P2.3 Maintain Financial Records

Manage billing and payment information.

### P2.4 Generate Management Reports

Prepare operational reports.

---

## Data Stores

### D4 – Google Sheets

Contains:

* Client information
* Project status
* Billing information

Issue:

Duplicate and inconsistent records.

---

### D5 – GitHub

Contains:

* Source code
* Issues
* Development activities

Issue:

Not connected to business records.

---

### D6 – Manual Documents

Contains:

* Reports
* Meeting records
* Project documents

Issue:

Version control problems.

---

## Data Flows

Project Manager → Project Data → P2.1

P2.1 → Store Data → D4

Developer → Code Updates → P2.2

P2.2 → Development Records → D5

Finance → Billing Information → P2.3

P2.3 → Financial Records → D4

P2.4 ← D4

P2.4 ← D5

P2.4 ← D6

P2.4 → Management Reports → Management

---

## Key Problems Visible

* No single source of truth.
* Data duplication across spreadsheets.
* Manual reconciliation required.
* Reporting requires data collection from multiple systems.
* High risk of inconsistent information.

---

### Recommendation for the report

For an ISAD course report, I would include:

1. **Context Diagram (Level 0)** — Whole Existing System.
2. **Level 1 DFD: Communication & Collaboration Subsystem.**
3. **Level 1 DFD: Data Management & Project Tracking Subsystem.**

These three diagrams are sufficient, directly support all five identified organizational problems, and are typically what lecturers expect in Chapter 4 analysis before moving to the proposed-system DFDs in later chapters.

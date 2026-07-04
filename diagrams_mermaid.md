# NextStepBD ISAD Report — Mermaid Diagram Source (Selected Figures)

This file contains the Mermaid source for the **14 node/edge diagrams** in
`report.tex` that are being replaced with rendered image files.

> **For each figure, do the following:**
> 1. Render the Mermaid block to PNG (e.g. via mermaid-cli, mermaid.live, or any
>    Mermaid renderer that supports `flowchart`, `graph`, and `erDiagram`).
> 2. Save the PNG to `images/<FILENAME>` (listed below each block).
> 3. Crop / tidy as needed — the original TikZ positions are intentionally
>    loose and may have whitespace that can be trimmed.
>
> After the images are in place, recompile `report.tex` — no other changes to
> the report are required.

## Filename scheme

`images/fig-{N}-{M}.png`

* `N` = chapter number
* `M` = figure number within the chapter (i.e. the rendered figure number is
  `N.M`)

So figure **4.17** → `images/fig-4-17.png`, figure **5.6** →
`images/fig-5-6.png`, etc.

## Figures included (14 total)

| Figure | Caption | File |
|---|---|---|
| 4.1 | Current Engineering & Delivery Workflow | `images/fig-4-1.png` |
| 4.2 | Current Billing and Support Workflows | `images/fig-4-2.png` |
| 4.17 | Level 1 DFD — Problem 1: Fragmented Communication & Collaboration | `images/fig-4-17.png` |
| 4.18 | Level 1 DFD — Problem 2: System Fragmentation & Lack of Integration | `images/fig-4-18.png` |
| 4.19 | Level 1 DFD — Problem 3: Data Management & Governance Deficiencies | `images/fig-4-19.png` |
| 4.20 | Level 1 DFD — Problem 4: Security & Access Control Risks | `images/fig-4-20.png` |
| 4.21 | Level 1 DFD — Problem 5: Scalability & Operational Bottlenecks | `images/fig-4-21.png` |
| 4.22 | Comparative Feasibility Framework — Three Alternative Solution Strategies | `images/fig-4-22.png` |
| 5.1 | Complete System DFD — the recommended new system on top of the existing context diagram | `images/fig-5-1.png` |
| 5.2 | Problem-Solving System DFD — side-by-side comparison (existing vs. new) | `images/fig-5-2.png` |
| 5.3 | Integration Core Subsystem DFD | `images/fig-5-3.png` |
| 5.4 | Configured Collaboration & Workflow Subsystem DFD | `images/fig-5-4.png` |
| 5.5 | DevOps, QA, and Observability Subsystem DFD | `images/fig-5-5.png` |
| 5.6 | ER Diagram — Canonical Data Model | `images/fig-5-6.png` |

## Rendering notes

* All diagrams are **Mermaid `flowchart` or `graph`** (left-to-right) unless
  marked otherwise.
* The ER diagram (Figure 5.6) uses Mermaid `erDiagram` syntax.
* Edge labels (`|"…"|>`) carry the original TikZ arrow labels.
* Subgraphs (`subgraph … end`) are used to reproduce group boxes (e.g.
  "Messaging", "Records", "Engineering" lanes).
* Shape syntax used:
  * `id["text"]` — rectangle (process / store / tool)
  * `id(("text"))` — circle (process bubbles, central node, problem badges)
  * `id[("text")]` — cylindrical (data stores in DFDs)
* Direction is `LR` (left-to-right) for DFDs and most workflow diagrams,
  and `TD` (top-down) for layered / framework diagrams.

---

## Figure 4.1 — Current Engineering & Delivery Workflow

**Filename:** `images/fig-4-1.png`

**Source location in `report.tex`:** lines 1978–2010 (pre-splice)
**LaTeX label:** (none)

```mermaid
graph TD
    CL(["Client"])
    PM["Project Manager"]
    SH[("Google Sheets")]
    DV["Developer"]
    GH[("GitHub")]
    CK["Developer / PM Check"]
    TL["Team Lead"]
    PR(("Production"))
    CL -- "WhatsApp / Email" --> PM
    PM -- "Manual Logging" --> SH
    PM -- "Assign Task" --> DV
    DV -- "Write Code" --> GH
    DV -- "Ad-hoc Test" --> CK
    CK -- "Chat Approval" --> TL
    TL -- "Manual Deploy" --> PR
    PR -- "Manual Notification" --> CL
```

---

## Figure 4.2 — Current Billing and Support Workflows

**Filename:** `images/fig-4-2.png`

**Source location in `report.tex`:** lines 2012–2049 (pre-splice)
**LaTeX label:** (none)

**Note:** Two subgraphs (Billing Process, Incident Management) with their
own actors / processes / stores.

```mermaid
graph LR
    subgraph BillingProcess["<b>Billing Process</b>"]
        S2[("Disparate Sheets")]
        PM2["Project Manager"]
        XL["Excel Invoice"]
        C2(["Client"])
        S2 -- "Compile Data" --> PM2
        PM2 -- "Manual Entry" --> XL
        XL -- "Email" --> C2
    end
    subgraph IncidentMgmt["<b>Incident Management</b>"]
        C3(["Client"])
        SUP["Developer / PM"]
        GH2[("GitHub")]
        C3 -- "Direct Chat" --> SUP
        SUP -- "Unstructured Fix" --> GH2
    end
```

---

## Figure 4.17 — Level 1 DFD: Problem 1 (Fragmented Communication & Collaboration)

**Filename:** `images/fig-4-17.png`

**Source location in `report.tex`:** lines 2988–3038 (pre-splice)
**LaTeX label:** `fig:dfd_prob1`

**Note:** Three informal-channel stores D1, D2, D3 are shared bidirectionally
between processes. Rendered as cylindrical data-store shapes.

```mermaid
graph LR
    CUST["Customer"]
    PM["Project Manager"]
    DEV["Developer"]
    QA["QA Engineer"]
    P11(("P1.1<br/>Receive via<br/>Informal Channels"))
    P12(("P1.2<br/>Interpret &amp;<br/>Forward (PM)"))
    P13(("P1.3<br/>Develop from<br/>Chat Notes"))
    P14(("P1.4<br/>Verify &amp;<br/>Approve in Chat"))
    P15(("P1.5<br/>Send Updates<br/>via Chat"))
    D1[("D1 | WhatsApp<br/>Messages")]
    D2[("D2 | Email<br/>Threads")]
    D3[("D3 | Ad-hoc<br/>Notes")]
    CUST -- "Requirements / Approvals" --> P11
    PM -- "Interprets" --> P12
    P11 -- "Raw messages" --> P12
    P12 -- "Verbal / chat tasks" --> DEV
    DEV -- "Progress" --> P13
    P13 -- "Completed work" --> P14
    QA -- "Verifies" --> P14
    P14 --> P15
    P15 -- "Status via chat" --> CUST
    P11 <--> D1
    P11 <--> D2
    P12 <--> D3
    P13 <--> D1
    P14 <--> D1
```

---

## Figure 4.18 — Level 1 DFD: Problem 2 (System Fragmentation & Lack of Integration)

**Filename:** `images/fig-4-18.png`

**Source location in `report.tex`:** lines 3051–3103 (pre-splice)
**LaTeX label:** `fig:dfd_prob2`

**Note:** Five disconnected data stores (D4–D8). The fragmentation is
implicit in the layout — none of D4–D8 share arrows with each other.

```mermaid
graph LR
    CUST["Customer"]
    PM["PM"]
    DEV["Developer"]
    FIN["Finance"]
    MGT["Management"]
    P21(("P2.1<br/>Log in<br/>Sheets"))
    P22(("P2.2<br/>Create<br/>GitHub Issue"))
    P23(("P2.3<br/>Update<br/>Status"))
    P24(("P2.4<br/>Record<br/>Billing"))
    P25(("P2.5<br/>Compile<br/>Reports"))
    D4[("D4 | Google Sheets")]
    D5[("D5 | GitHub")]
    D6[("D6 | WhatsApp")]
    D7[("D7 | Email")]
    D8[("D8 | Manual Docs")]
    CUST -- "Request" --> P21
    PM -- "Copy to" --> P21
    P21 -- "Manual copy" --> P22
    DEV -- "Progress" --> P23
    P23 -- "Re-enter" --> P24
    FIN -- "Billing data" --> P24
    P24 -- "Export" --> P25
    P25 -- "Reports" --> MGT
    P21 <--> D4
    P22 <--> D5
    P23 <--> D6
    P23 <--> D7
    P25 <--> D8
```

---

## Figure 4.19 — Level 1 DFD: Problem 3 (Data Management & Governance Deficiencies)

**Filename:** `images/fig-4-19.png`

**Source location in `report.tex`:** lines 3116–3166 (pre-splice)
**LaTeX label:** `fig:dfd_prob3`

```mermaid
graph LR
    PM["Project Manager"]
    DEV["Developer"]
    FIN["Finance"]
    MGT["Management"]
    P31(("P3.1<br/>Maintain<br/>Customer List"))
    P32(("P3.2<br/>Track<br/>Project Data"))
    P33(("P3.3<br/>Update<br/>Billing"))
    P34(("P3.4<br/>Reconcile<br/>&amp; Report"))
    D9[("D9 | Sheets -<br/>Customers")]
    D10[("D10 | Sheets -<br/>Projects")]
    D11[("D11 | GitHub<br/>Projects")]
    D12[("D12 | Billing<br/>Sheet")]
    D13[("D13 | Master<br/>Report (manual)")]
    PM -- "Update customer" --> P31
    DEV -- "Project status" --> P32
    FIN -- "Invoice data" --> P33
    P31 -- "Copy" --> P34
    P32 -- "Copy" --> P34
    P33 -- "Copy" --> P34
    P34 -- "Inconsistent report" --> MGT
    P31 <--> D9
    P31 <--> D10
    P32 <--> D10
    P32 <--> D11
    P33 <--> D12
    P34 <--> D13
```

---

## Figure 4.20 — Level 1 DFD: Problem 4 (Security & Access Control Risks)

**Filename:** `images/fig-4-20.png`

**Source location in `report.tex`:** lines 3179–3226 (pre-splice)
**LaTeX label:** `fig:dfd_prob4`

```mermaid
graph LR
    CUST["Customer"]
    PM["Project Manager"]
    DEV["Developer"]
    FIN["Finance"]
    CEO["CEO / Legal"]
    P41(("P4.1<br/>Share via<br/>Chat"))
    P42(("P4.2<br/>Forward<br/>Credentials"))
    P43(("P4.3<br/>Store in<br/>Personal Docs"))
    P44(("P4.4<br/>Access<br/>Ad-hoc"))
    D14[("D14 | WhatsApp<br/>Groups")]
    D15[("D15 | Email<br/>Attachments")]
    D16[("D16 | Local<br/>Drives")]
    D17[("D17 | Shared Folders<br/>(no ACL)")]
    CUST -- "PII / Contract" --> P41
    PM -- "Credentials" --> P42
    P41 -- "Forward" --> P42
    DEV -- "Client data" --> P43
    FIN -- "Financials" --> P44
    P43 -- "Access" --> P44
    P41 <--> D14
    P42 <--> D15
    P43 <--> D16
    P44 <--> D17
```

---

## Figure 4.21 — Level 1 DFD: Problem 5 (Scalability & Operational Bottlenecks)

**Filename:** `images/fig-4-21.png`

**Source location in `report.tex`:** lines 3239–3291 (pre-splice)
**LaTeX label:** `fig:dfd_prob5`

```mermaid
graph LR
    CUST["Customer"]
    PM["Project Manager"]
    DEV1["Developer A"]
    DEV2["Developer B"]
    QA["QA"]
    HR["HR / Onboarding"]
    P51(("P5.1<br/>Route All<br/>Requests"))
    P52(("P5.2<br/>Manual Task<br/>Assignment"))
    P53(("P5.3<br/>Chase<br/>Updates"))
    P54(("P5.4<br/>Approve &amp;<br/>Onboard"))
    D18[("D18 | PM's<br/>Personal Notes")]
    D19[("D19 | Chat History<br/>(PM only)")]
    D20[("D20 | Email<br/>(PM inbox)")]
    CUST -- "Any request" --> P51
    P51 -- "Only via PM" --> PM
    PM -- "Assign" --> P52
    P52 -- "Task" --> DEV1
    P52 -- "Task" --> DEV2
    DEV1 -- "Status?" --> P53
    DEV2 -- "Status?" --> P53
    QA -- "Ready?" --> P53
    P53 -- "Report back" --> PM
    PM -- "Final approval" --> P54
    P54 -- "New staff" --> HR
    P51 <--> D18
    P52 <--> D19
    P53 <--> D20
    P54 <--> D18
```

---

## Figure 4.22 — Comparative Feasibility Framework

**Filename:** `images/fig-4-22.png`

**Source location in `report.tex`:** lines 3343–3406 (pre-splice)
**LaTeX label:** `fig:feasibility-framework`

**Note:** Five problems across the top, three strategy boxes in the
middle, three feasibility lenses below, decision node, and design
handoff at the bottom. Edges from each problem fan out to each of the
three strategies (Mermaid will render these as 15 thin arrows; the
visual clutter is acceptable because the message is "all five problems
feed all three strategies").

```mermaid
graph TD
    P1["Fragmented<br/>Communication"]
    P2["System<br/>Fragmentation"]
    P3["Data Governance<br/>Deficiencies"]
    P4["Security &amp; Access<br/>Control Risks"]
    P5["Scalability<br/>Bottlenecks"]
    SBUY["<b>Strategy 1: BUY</b><br/>Off-the-shelf enterprise suite"]
    SCONF["<b>Strategy 2: CONFIGURE</b><br/>Best-of-breed tools + small core"]
    SBUILD["<b>Strategy 3: BUILD</b><br/>Custom in-house platform"]
    T["Technical"]
    E["Economic"]
    O["Operational &amp; Schedule"]
    D["<b>Comparative Selection</b><br/>&amp; Recommendation"]
    R["<b>Design Handoff to Chapter 5</b><br/>Requirements, Migration, Rollout, and Governance"]
    P1 --> SBUY
    P1 --> SCONF
    P1 --> SBUILD
    P2 --> SBUY
    P2 --> SCONF
    P2 --> SBUILD
    P3 --> SBUY
    P3 --> SCONF
    P3 --> SBUILD
    P4 --> SBUY
    P4 --> SCONF
    P4 --> SBUILD
    P5 --> SBUY
    P5 --> SCONF
    P5 --> SBUILD
    SBUY --> T
    SCONF --> E
    SBUILD --> O
    T --> D
    E --> D
    O --> D
    D --> R
```

---

## Figure 5.1 — Complete System DFD (new system on top of existing context diagram)

**Filename:** `images/fig-5-1.png`

**Source location in `report.tex`:** lines 4200–4309 (pre-splice)
**LaTeX label:** `fig:dfd-complete-system`

**Note:** External entities (E1–E4) match the Ch4 context diagram
positions. The undifferentiated process P0 is replaced by three new
processes (P-new-collab, P-new-core, P-new-devops) and one canonical
store (D-canonical). Legacy stores D1–D13 and legacy process P0 are
shown faded on the right. Cross-cutting controls wrap the new
architecture.

```mermaid
graph LR
    CUST["<b>E1</b><br/>Customers"]
    CEO["<b>E2</b><br/>Management<br/>(CEO)"]
    EMP["<b>E3</b><br/>Employees"]
    HR["<b>E4</b><br/>HR<br/>Department"]
    DCANON["<b>D-canonical</b><br/>Canonical Store:<br/>Customer, Project, Requirement,<br/>Approval, Task, BillingRecord,<br/>Incident, AuditLog"]
    PCOLLAB["P-new-collab<br/>Configured<br/>Collaboration<br/>&amp; Workflow"]
    PCORE["P-new-core<br/>Integration<br/>Core<br/>(API, Webhooks,<br/>Review Queue)"]
    PDEVOPS["P-new-devops<br/>DevOps, QA<br/>&amp; Observability"]
    LSTORE["Legacy stores D1–D13<br/>(from Ch.4): WhatsApp, Email,<br/>Sheets, GitHub, Ad-hoc Notes,<br/>PM's Personal Notes"]
    P0LEGACY["(legacy) P0<br/>Existing Manual<br/>Procedures<br/>(informal)"]
    SEC["<b>Cross-Cutting Controls</b><br/>Identity, RBAC, Audit Log,<br/>Redaction, Data Quality,<br/>Backup, Monitoring"]
    CUST -- "Requirements, Approvals,<br/>Payments" --> DCANON
    DCANON -- "Deliverables,<br/>Invoices, Updates" --> CUST
    CEO -- "Policies, Decisions" --> PCORE
    PCORE -- "Reports" --> CEO
    EMP -- "Task Updates" --> PCOLLAB
    PCOLLAB -- "Tasks, Instructions" --> EMP
    HR -- "Employee<br/>Information" --> PCORE
    PCORE -- "Staffing<br/>Requests" --> HR
    PCOLLAB --> DCANON
    PCORE --> DCANON
    PDEVOPS --> DCANON
    PCORE -. "Two-way sync" .-> LSTORE
    LSTORE -. "continues in use" .-> DCANON
    P0LEGACY -. "replaced" .-> PCORE
    SEC --> PCOLLAB
    SEC --> PCORE
    SEC --> PDEVOPS
```

---

## Figure 5.2 — Problem-Solving System DFD (side-by-side: existing vs. new)

**Filename:** `images/fig-5-2.png`

**Source location in `report.tex`:** lines 4347–4463 (pre-splice)
**LaTeX label:** `fig:dfd-problem-solving`

**Note:** Left half is the existing system (Ch.4 context diagram
mirrored). Right half is the new system (P-new-collab / P-new-core /
P-new-devops with the canonical store and the P4 cross-cutting halo).
Problem badges (P1–P5) are shown as small circle nodes near the new
flows they address. A dashed migration arrow connects "P0 (existing)"
to the new system.

```mermaid
graph LR
    %% ===== Existing system (left) =====
    subgraph ExistingSys["<b>Existing System (Ch.4)</b>"]
        E1L["<b>E1</b><br/>Customers"]
        E2L["<b>E2</b><br/>Management"]
        E3L["<b>E3</b><br/>Employees"]
        E4L["<b>E4</b><br/>HR"]
        P0L(("P0<br/>Existing System<br/>(informal + manual)"))
        E1L -- "Requirements,<br/>Approvals" --> P0L
        P0L -- "Deliverables,<br/>Updates" --> E1L
        E2L -- "Policies" --> P0L
        P0L -- "Reports" --> E2L
        E3L -- "Updates" --> P0L
        P0L -- "Tasks" --> E3L
        E4L -- "Staffing" --> P0L
        P0L -- "Employee info" --> E4L
    end

    %% Migration arrow
    P0L -. "legacy P0 replaced by new system" .-> NewCore

    %% ===== New system (right) =====
    subgraph NewSys["<b>New System (Ch.5 — Configure)</b>"]
        PCOLLAB["P-new-collab<br/>Collaboration<br/>&amp; Workflow"]
        PCORE["P-new-core<br/>Integration<br/>Core"]
        PDEVOPS["P-new-devops<br/>DevOps,<br/>QA &amp; Obs."]
        CANON["D-canonical<br/>Customer,<br/>Project, Req,<br/>Task, …"]
        E1R["<b>E1</b><br/>Customers"]
        E2R["<b>E2</b><br/>Management"]
        E3R["<b>E3</b><br/>Employees"]
        E4R["<b>E4</b><br/>HR"]
        P1T(("P1"))
        P2T(("P2"))
        P3T(("P3"))
        P4T(("P4"))
        P5T(("P5"))

        E1R -- "Requirements (P1)" --> PCOLLAB
        PCOLLAB -- "Deliverables" --> E1R
        E2R -- "Policies" --> PCORE
        PCORE -- "Reports (P3)" --> E2R
        E3R -- "Updates" --> PDEVOPS
        PDEVOPS -- "Tasks (P5)" --> E3R
        E4R -- "Employee info" --> PCORE
        PCORE -- "Staffing" --> E4R
        PCOLLAB -- "Req/Approval (P2)" --> CANON
        PCORE -- "Sync (P3)" --> CANON
        PDEVOPS -- "Release evidence (P2)" --> CANON
    end
```

---

## Figure 5.3 — Integration Core Subsystem DFD

**Filename:** `images/fig-5-3.png`

**Source location in `report.tex`:** lines 4584–4648 (pre-splice)
**LaTeX label:** `fig:dfd-integration-core`

```mermaid
graph LR
    WA["WhatsApp / Slack"]
    SH["Sheets / Excel"]
    GIT["GitHub"]
    EM["Email"]
    GW["P1.1<br/>API &amp; Webhook<br/>Gateway"]
    VAL["P1.2<br/>Validate<br/>&amp; Dedupe"]
    REV["P1.3<br/>Operator Review<br/>Queue"]
    CANON["D1<br/>Canonical Store<br/>(Customer, Project,<br/>Requirement, Approval,<br/>Task, Billing,<br/>Incident, Audit)"]
    AUD["Audit Log<br/>&amp; Lineage"]
    IAM["Identity<br/>&amp; RBAC"]
    DASH["Reporting<br/>&amp; Dashboards"]
    DQ["Data Quality<br/>&amp; Reconciliation"]
    WA --> GW
    SH --> GW
    GIT --> GW
    EM --> GW
    GW --> VAL
    GW --> REV
    VAL --> CANON
    REV --> CANON
    CANON --> AUD
    CANON --> IAM
    CANON --> DASH
    CANON --> DQ
```

---

## Figure 5.4 — Configured Collaboration & Workflow Subsystem DFD

**Filename:** `images/fig-5-4.png`

**Source location in `report.tex`:** lines 4691–4752 (pre-splice)
**LaTeX label:** `fig:dfd-collaboration`

```mermaid
graph LR
    CL["Client"]
    PM["Project Manager"]
    DV["Developer / QA"]
    INTAKE["P2.1<br/>Requirement<br/>Intake"]
    APPROVE["P2.2<br/>Approval<br/>Capture"]
    TASK["P2.3<br/>Task<br/>Assignment"]
    ESCALATE["P2.4<br/>Escalation<br/>&amp; Reminder"]
    ONBOARD["P2.5<br/>Onboarding<br/>Workflow"]
    TEMPLATE["P2.6<br/>Template<br/>Library"]
    ISSUE["D2<br/>Issue / Ticket<br/>Repository"]
    CONF["D3<br/>Workflow<br/>Configuration"]
    KNOW["D4<br/>Knowledge<br/>Base"]
    CL --> INTAKE
    PM --> APPROVE
    PM --> TASK
    DV --> TASK
    INTAKE --> APPROVE
    INTAKE --> TEMPLATE
    APPROVE --> ESCALATE
    APPROVE --> TEMPLATE
    TASK --> ESCALATE
    TASK --> TEMPLATE
    INTAKE --> ISSUE
    APPROVE --> ISSUE
    TASK --> ISSUE
    ESCALATE --> CONF
    ONBOARD --> KNOW
    TEMPLATE --> CONF
```

---

## Figure 5.5 — DevOps, QA, and Observability Subsystem DFD

**Filename:** `images/fig-5-5.png`

**Source location in `report.tex`:** lines 4813–4879 (pre-splice)
**LaTeX label:** `fig:dfd-devops`

```mermaid
graph LR
    DEV["Developer"]
    QA["QA Engineer"]
    SRE["SRE / Lead"]
    COMMIT["P3.1<br/>Commit<br/>&amp; Branch"]
    CI["P3.2<br/>CI Build<br/>&amp; Tests"]
    SEC["P3.3<br/>Security<br/>&amp; Quality"]
    STAGE["P3.4<br/>Staging<br/>Deploy"]
    REL["P3.5<br/>Release<br/>Approval"]
    PROD["P3.6<br/>Production"]
    MON["P3.7<br/>Monitor<br/>&amp; Alert"]
    INC["P3.8<br/>Incident<br/>Workflow"]
    RB["P3.9<br/>Rollback"]
    REPO["D5<br/>Source<br/>Repository"]
    ART["D6<br/>Artifact<br/>Registry"]
    LOGS["D7<br/>Logs / Metrics<br/>Registry"]
    TICK["D8<br/>Incident<br/>Tickets"]
    DEV --> COMMIT
    COMMIT --> CI
    CI --> SEC
    SEC --> STAGE
    STAGE --> REL
    REL --> PROD
    PROD --> MON
    MON --> INC
    INC --> RB
    RB --> STAGE
    COMMIT --> REPO
    CI --> ART
    MON --> LOGS
    INC --> TICK
    QA --> SEC
    SRE --> PROD
```

---

## Figure 5.6 — ER Diagram (Canonical Data Model)

**Filename:** `images/fig-5-6.png`

**Source location in `report.tex`:** lines 4989–5043 (pre-splice)
**LaTeX label:** `fig:er-diagram`

**Note:** Uses Mermaid `erDiagram` syntax (the only diagram in the
report that does). Cardinalities follow the original TikZ labels:
"1" for single, "1..N" for one-to-many, "0..N" for optional many.

```mermaid
erDiagram
    CUSTOMER ||--o{ REQUIREMENT : "1 → 0..N"
    PROJECT ||--o{ REQUIREMENT : "1 → 0..N"
    REQUIREMENT ||--o{ APPROVAL : "0..N"
    REQUIREMENT ||--o{ TASK : "1..N"
    EMPLOYEE ||--o{ TASK : "1"
    USER ||--o{ AUDITLOG : "1..N"
    TASK ||--o{ BILLINGRECORD : "0..N"
    TASK ||--o{ INCIDENT : "0..N"
    APPROVAL ||--o{ AUDITLOG : "0..N"
    REQUIREMENT ||--o{ AUDITLOG : "0..N"
    SOURCEMESSAGE ||--o{ REQUIREMENT : "0..N"
    SOURCEMESSAGE ||--o{ APPROVAL : "0..N"
    SOURCEMESSAGE ||--o{ TASK : "0..N"
    CROSSCUTTING ||--o{ AUDITLOG : ""
    CROSSCUTTING ||--o{ USER : ""

    CUSTOMER {
        string id PK
        string name
        string contact
    }
    PROJECT {
        string id PK
        string name
        string customer_id FK
    }
    REQUIREMENT {
        string id PK
        string project_id FK
        string source_message_id FK
        text description
    }
    APPROVAL {
        string id PK
        string requirement_id FK
        string approver_user_id FK
        string decision
        datetime decided_at
    }
    TASK {
        string id PK
        string requirement_id FK
        string assignee_user_id FK
        string status
    }
    EMPLOYEE {
        string id PK
        string user_id FK
        string role
    }
    USER {
        string id PK
        string role
    }
    BILLINGRECORD {
        string id PK
        string task_id FK
        decimal amount
    }
    INCIDENT {
        string id PK
        string task_id FK
        text description
    }
    AUDITLOG {
        string id PK
        string actor_user_id FK
        string entity
        datetime at
    }
    SOURCEMESSAGE {
        string id PK
        string channel
        text body
    }
    CROSSCUTTING {
        string id PK
        string control_name
    }
```

---

# End of diagrams

When all 14 PNGs are placed under `images/`, recompile `report.tex` (the
LaTeX file is already updated to reference these filenames via
`\includegraphics{images/<FILENAME>}`).

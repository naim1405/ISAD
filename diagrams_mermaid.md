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
| 5.2 | Level 1 DFD — Problem 1: Fragmented Communication & Collaboration | `images/fig-5-2.png` |
| 5.3 | Level 1 DFD — Problem 2: System Fragmentation & Lack of Integration | `images/fig-5-3.png` |
| 5.4 | Level 1 DFD — Problem 3: Data Management & Governance Deficiencies | `images/fig-5-4.png` |
| 5.5 | Level 1 DFD — Problem 4: Security & Access Control Risks | `images/fig-5-5.png` |
| 5.6 | Level 1 DFD — Problem 5: Scalability & Operational Bottlenecks | `images/fig-5-6.png` |
| 5.7 | ER Diagram — Canonical Data Model | `images/fig-5-7.png` |

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


# p1_old_system_dfd:
```mermaid
flowchart TD

    CUST[Customer]
    PM[Project Manager]
    DEV[Developer]
    QA[QA Engineer]

    P11((1.1 Receive Requirements))
    P12((1.2 Interpret Requirements))
    P13((1.3 Development))
    P14((1.4 Verification & Approval))
    P15((1.5 Client Updates))

    D1[(D1 Requirements)]
    D2[(D2 Email Records)]
    D3[(D3 Project Notes)]

    CUST -->|Requirements| P11
    P11 -->|Raw Requests| P12
    PM -->|Interpretation| P12

    P12 -->|Development Tasks| P13
    DEV -->|Progress| P13

    P13 -->|Completed Work| P14
    QA -->|Verification| P14

    P14 --> P15
    P15 -->|Project Updates| CUST

    P11 <--> D1
    P11 <--> D2
    P12 <--> D3
    P13 <--> D1
    P14 <--> D1
```

# p1_new_system_dfd:
```mermaid
flowchart TD

    CUST[Customer]
    PM[Project Manager]
    DEV[Developer]
    QA[QA Engineer]

    P11((1.1 Client Intake))
    P12((1.2 Requirement Review))
    P21((2.1 Task Assignment))
    P22((2.2 Development))
    P23((2.3 Verification & Approval))
    P13((1.3 Client Updates))

    D1[(D1 Requirements & Tasks)]

    CUST -->|Requirement Form| P11
    P11 -->|Validated Requirement| P12
    PM -->|Approval| P12

    P12 -->|Approved Task| P21
    P21 -->|Assigned Work| P22
    DEV -->|Completed Work| P22

    P22 -->|Completed Task| P23
    QA -->|Verification| P23

    P23 --> P13
    P13 -->|Status Updates| CUST

    P11 --> D1
    P12 --> D1
    P21 --> D1
    P22 --> D1
    P23 --> D1
    P13 --> D1

```

# p2_old_system_dfd:
```mermaid
flowchart TD

    CUST[Customer]
    PM[Project Manager]
    DEV[Developer]
    FIN[Finance]
    MGT[Management]

    P21((2.1 Log Project Data))
    P22((2.2 Create GitHub Issue))
    P23((2.3 Update Project Status))
    P24((2.4 Record Billing))
    P25((2.5 Generate Reports))

    D1[(D1 Project Records)]
    D2[(D2 GitHub Repository)]
    D3[(D3 Communication Records)]
    D4[(D4 Reports)]

    CUST -->|Request| P21
    PM -->|Project Details| P21

    P21 -->|Manual Entry| P22
    DEV -->|Development Progress| P23

    P23 -->|Status Updates| P24
    FIN -->|Billing Data| P24

    P24 -->|Billing Information| P25
    P25 -->|Reports| MGT

    P21 <--> D1
    P22 <--> D2
    P23 <--> D3
    P25 <--> D4

```
# p2_new_system_dfd:
```mermaid
flowchart TD

    CUST[Customer]
    PM[Project Manager]
    DEV[Developer]
    FIN[Finance]
    MGT[Management]

    P21((2.1 Capture Project Data))
    P22((2.2 Create & Assign Tasks))
    P23((2.3 Track Project Status))
    P24((2.4 Capture Billing))
    P25((2.5 Generate Reports))

    D1[(D1 Project Information Repository)]

    CUST -->|Request| P21
    PM -->|Project Details| P21

    P21 -->|Validated Project Data| P22
    DEV -->|Task Progress| P23

    P22 --> D1
    P23 --> D1

    FIN -->|Billing Data| P24
    P24 --> D1

    D1 --> P25
    P25 -->|Reports| MGT

```


# p3_old_system_dfd:
```mermaid
flowchart TD

    PM[Project Manager]
    DEV[Developer]
    FIN[Finance]
    MGT[Management]

    P31((3.1 Customer Management))
    P32((3.2 Project Tracking))
    P33((3.3 Billing))
    P34((3.4 Reporting))

    D1[(D1 Customer Records)]
    D2[(D2 Project Records)]
    D3[(D3 GitHub Projects)]
    D4[(D4 Billing Records)]
    D5[(D5 Master Report)]

    PM -->|Customer Details| P31
    DEV -->|Project Status| P32
    FIN -->|Invoice Data| P33

    P31 <--> D1
    P31 <--> D2

    P32 <--> D2
    P32 <--> D3

    P33 <--> D4

    D1 --> P34
    D2 --> P34
    D3 --> P34
    D4 --> P34

    P34 --> D5
    P34 -->|Reports| MGT

```



# p3_new_system_dfd:
```mermaid
flowchart TD

    PM[Project Manager]
    DEV[Developer]
    FIN[Finance]
    MGT[Management]

    P11((1.1 Requirement & Project Creation))
    P21((2.1 Task Assignment & Project Tracking))
    P31((3.1 Billing Capture))
    P41((4.1 Reporting & Reconciliation))

    D1[(D1 Canonical Data Store)]

    C1[RBAC, Audit Log, Validation]

    PM -->|Requirement Details| P11
    DEV -->|Task & Status Updates| P21
    FIN -->|Billing Information| P31

    P11 --> D1
    P21 --> D1
    P31 --> D1

    D1 --> P41
    P41 -->|Reports| MGT

    C1 -.-> D1
```




# p4_old_system_dfd:
```mermaid
flowchart TD

    CUST[Customer]
    PM[Project Manager]
    DEV[Developer]
    FIN[Finance]
    CEO[CEO / Legal]

    P41((4.1 Receive Sensitive Data))
    P42((4.2 Share Credentials))
    P43((4.3 Store Project Files))
    P44((4.4 Access Information))

    D1[(D1 Chat Records)]
    D2[(D2 Email Records)]
    D3[(D3 Local Files)]
    D4[(D4 Shared Files)]

    CUST -->|PII & Contracts| P41
    P41 -->|Forward Data| P42
    PM -->|Credentials| P42

    DEV -->|Project Files| P43
    P43 -->|Stored Files| P44

    FIN -->|Financial Data| P44

    P41 <--> D1
    P42 <--> D2
    P43 <--> D3
    P44 <--> D4

```
# p4_new_system_dfd:
```mermaid
flowchart TD

    CUST[Customer]
    PM[Project Manager]
    DEV[Developer]
    FIN[Finance]
    CEO[CEO / Legal]

    P41((5.1 Secure Client Intake))
    P42((5.2 Credential Management))
    P43((5.3 Access Management))
    P44((5.4 Audit & Compliance))

    D1[(D1 Secure Information Repository)]

    CUST -->|Customer Information| P41
    P41 --> D1

    PM -->|Credential Requests| P42
    P42 --> D1

    DEV -->|Access Requests| P43
    P43 --> D1

    FIN -->|Financial Information| P44
    D1 --> P44

    P44 -->|Compliance Reports| CEO

```





# p5_old_system_dfd:
```mermaid
flowchart TD

    CUST[Customer]
    PM[Project Manager]
    DEV1[Developer A]
    DEV2[Developer B]
    QA[QA Engineer]
    HR[HR]

    P51((5.1 Receive Requests))
    P52((5.2 Assign Tasks))
    P53((5.3 Track Progress))
    P54((5.4 Approval & Onboarding))

    D1[(D1 PM Notes)]
    D2[(D2 Communication Records)]
    D3[(D3 Email Records)]

    CUST -->|Requests| P51
    P51 -->|Forward Requests| PM

    PM -->|Assign Tasks| P52

    P52 -->|Tasks| DEV1
    P52 -->|Tasks| DEV2

    DEV1 -->|Progress| P53
    DEV2 -->|Progress| P53
    QA -->|Verification| P53

    P53 -->|Status Report| PM

    PM -->|Approval| P54
    P54 -->|Onboarding| HR

    P51 <--> D1
    P52 <--> D2
    P53 <--> D3
    P54 <--> D1
```
# p5_new_system_dfd:

```mermaid
flowchart TD

    CUST[Customer]
    PM[Project Manager]
    DEV1[Developer A]
    DEV2[Developer B]
    QA[QA Engineer]
    HR[HR]

    P51((5.1 Route Requests))
    P52((5.2 Assign Tasks))
    P53((5.3 Track Progress))
    P54((5.4 Approval & Onboarding))

    D1[(D1 Project Management Repository)]

    CUST -->|Requests| P51

    P51 -->|Validated Request| P52
    PM -->|Task Approval| P52

    P52 -->|Assigned Task| DEV1
    P52 -->|Assigned Task| DEV2

    DEV1 -->|Progress Updates| P53
    DEV2 -->|Progress Updates| P53
    QA -->|Verification| P53

    P53 --> D1
    D1 -->|Progress Reports| PM

    PM -->|Approval| P54
    P54 --> D1

    P54 -->|Onboarding| HR

```


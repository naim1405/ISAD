# ISAD Project Checkpoint

**Date:** May 2, 2026
**Target Document:** `main.tex`

## Current Status
- **Completed Chapters:**
  - **Chapter 1: Recognition of Need** (Company background, current workflow, and problem identification)
  - **Chapter 2: Initial Feasibility Study** (Operational, Technical, and Economic feasibility analysis including TEO metrics, severity charts, and current operational swimlane diagrams)
- **Pending Work:**
  - **Chapter 3: System Modeling** (Use Case Diagrams, DFDs, ER Models)
  - Subsequent chapters for design, implementation, and conclusion.

## Company Profile
**NextStepBD** is a Bangladesh-based technology company specializing in custom software development, AI support platforms, and workflow automation. They have a flat organizational structure and rely on high agility. 
**Current State:** They rely on fractured systems (WhatsApp, Slack, GitHub, Excel) resulting in significant operational overhead, manual data transfers, and a heavy reliance on a few key project managers. 
**Objective:** Design and propose an integrated information system to centralize operations, requirement tracking, and delivery.

## Core Problems Identified (The Focus of the Report)
We have isolated and are solving the following **Top 5 Core System Failures**:
1. **Problem 01:** Fragmented System Architecture and Lack of Integration
2. **Problem 02:** The Project Manager Bottleneck and Central Dependency
3. **Problem 03:** Unstructured Requirement Gathering and Scope Creep
4. **Problem 04:** Absence of a Centralized Task Tracking System
5. **Problem 05:** Quality Assurance and Deployment Vulnerabilities

## Technical Specs & Progress
- **LaTeX Setup:** `report` document class, utilizing `tcolorbox` for highlighting, `tabularx` for tables, and `tikz`/`pgfplots` for complex diagrams. 
- **Compilation Status:** All fatal errors (like `pgfkeys` step conflicts) and geometry warnings (`\headheight`) have been resolved. The PDF builds perfectly.
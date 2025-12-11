# Quotech Current State — UI/UX Mapping

> **Document Status**: Active Documentation  
> **Last Updated**: December 2024  
> **Source**: Screenshots from existing Quotech application  
> **Purpose**: Map the current state of Quotech to inform future development decisions

---

## Table of Contents

### Core Application
1. [Global Navigation & Layout](#1-global-navigation--layout)
2. [All Active Jobs List View](#2-all-active-jobs-list-view)

### Job Detail Tabs
3. [Job Detail View — Summary Tab](#3-job-detail-view--summary-tab)
4. [Job Detail View — Labour Tab](#4-job-detail-view--labour-tab)
5. [Job Detail View — Materials Tab](#5-job-detail-view--materials-tab)
6. [Job Detail View — Equipment Tab](#6-job-detail-view--equipment-tab)
7. [Job Detail View — Subcontractors Tab](#7-job-detail-view--subcontractors-tab)
8. [Job Detail View — Others Tab](#8-job-detail-view--others-tab)
9. [Job Detail View — Quote Sheet Tab](#9-job-detail-view--quote-sheet-tab)
10. [AI Insights Side Panel](#10-ai-insights-side-panel)
11. [Summary Dashboard (Cost Breakdown)](#11-summary-dashboard-additional-view)
12. [Notes Section](#12-notes-section-all-tabs)

### Quotations Module
14. [All Quotations Module](#14-all-quotations-module)

### Reports Module
15. [Reports Module Overview](#15-reports-module)
16. [Job Performance Summary Report](#16-job-performance-summary-report)
17. [Pro-rata Analysis Report](#17-pro-rata-analysis-report)
18. [Financial Report](#18-financial-report)
19. [Man Hours Report](#19-man-hours-report)
20. [Chargeout Projection Report](#20-chargeout-projection-report)

### User Management & Settings
21. [Users Module](#21-users-module)
22. [Job Summary — Alternative View](#22-job-summary--alternative-view-cost-breakdown)
23. [Settings Module](#23-settings-module)

### Reference
24. [Data Model Observations](#24-data-model-observations)
25. [UX Patterns & Components](#25-ux-patterns--components)
26. [AI Features](#26-ai-features)
27. [Open Questions & Gaps](#27-open-questions--gaps)

---

## 1. Global Navigation & Layout

### 1.1 Application Shell

```
┌─────────────────────────────────────────────────────────────────────────┐
│ QUOTECH                                      🔔(50) 👤 ☀️              │
│ [Company Selector ▼]                                                     │
├────────────────────┬────────────────────────────────────────────────────┤
│                    │                                                     │
│  🏠 Active Jobs  > │                                                     │
│                    │                   MAIN CONTENT AREA                 │
│  📊 Reports      > │                                                     │
│                    │                                                     │
│  📄 Quotations   > │                                                     │
│                    │                                                     │
│  👥 Users          │                                                     │
│                    │                                                     │
│  ⚙️ Setting        │                                                     │
│                    │                                                     │
│  ➡️ Logout         │                                                     │
│                    │                                                     │
│                    │                                                     │
│                    │                                                     │
│ [□ Hide Labels]    │                                                     │
└────────────────────┴────────────────────────────────────────────────────┘
```

### 1.2 Header Components

| Component | Description | Location |
|-----------|-------------|----------|
| **Logo** | "QUOTECH" branding | Top-left |
| **Company Selector** | Dropdown to switch companies (e.g., "Bravada Group Pty Ltd") | Below logo |
| **Notifications Bell** | Shows count badge (50) | Top-right |
| **User Avatar** | Profile picture/avatar | Top-right |
| **Theme Toggle** | Light/dark mode switch (☀️) | Top-right |

### 1.3 Sidebar Navigation

| Menu Item | Icon | Has Submenu | Description |
|-----------|------|-------------|-------------|
| **Active Jobs** | 🏠 | Yes (>) | Main job management hub |
| **Reports** | 📊 | Yes (>) | Business intelligence & reporting |
| **Quotations** | 📄 | Yes (>) | Quote/tender management |
| **Users** | 👥 | No | User management |
| **Setting** | ⚙️ | No | System configuration |
| **Logout** | ➡️ | No | Session logout |

**Sidebar Features:**
- Collapsible labels via "Hide Labels" toggle at bottom
- Visual indicator (>) for expandable menu items
- Collapsed state shows only icons

---

## 2. All Active Jobs List View

### 2.1 Page Header

```
Page Title: "All Active Jobs"
```

### 2.2 Filter Bar

| Filter | Type | Options/Behavior |
|--------|------|------------------|
| **Status** | Dropdown | "Active Works" (default), likely others |
| **Select Date Range** | Date picker | Calendar icon, range selection |
| **Project Manager** | Dropdown | "All" default, list of PMs |
| **Page Size** | Dropdown | "50 per page" default |
| **Search jobs...** | Text input | Free-text search |

### 2.3 Active Filters Display

- Chip-style display showing active filters
- Example: `Active Filters: [Active Works ✕]`
- "Clear Filters" button (red/coral color) to reset all

### 2.4 Jobs Data Table

#### Column Structure

| Column | Sortable | Data Type | Notes |
|--------|----------|-----------|-------|
| **Project Manager** | Yes (↓) | Text with badge | Shows badges: "Labour Loss" (red), "Ongoing" (green) |
| **Job no.** | Yes (↓) | Text | Format: J#### (e.g., J5955) |
| **Start** | Yes (↓) | Date | Format: DD MMM YY |
| **End** | Yes (↓) | Date | "-" for ongoing jobs |
| **Status** | Yes (↓) | Dropdown/Badge | "Active Works" with selector (↕) |
| **Revenue** | Yes (↓) | Currency | Format: $#,###,### |
| **WIP** | Yes (↓) | Currency | Work in Progress value |
| **Client Name** | Yes (↓) | Text | Company name |
| **Site Address** | No | Text | Project location |
| **% C[ompletion]** | No | Progress indicator | Circular progress with percentage |

#### Row Data Examples

| Job | PM | Start | Status | Revenue | WIP | Client | % Complete |
|-----|-----|-------|--------|---------|-----|--------|------------|
| J5955 | PU SUP Uriah Gray | 22 Aug 24 | Active Works | $2,708,385 | $1,485,806 | SPARK Consortium | 45% |
| J6466 | PU SUP Daniel May | 27 Aug 25 | Active Works | $1,326,102 | $1,173,564 | North Western Program Alliance | 12% |
| J6234 | PU SUP Michael Fol... | 22 Oct 24 | Active Works | $5,014,326 | $1,039,342 | SPARK Consortium | 79% |
| J6499 | PU SUP Ben Sharland | 09 Oct 25 | Active Works | $841,395 | $799,587 | Delta Pty Ltd | 55% |
| J6379 | PU SUP Daniel May | 29 May 25 | Active Works | $549,868 | $534,410 | Spence Construction | 35% |

#### Status Badges

| Badge | Color | Meaning |
|-------|-------|---------|
| **Labour Loss** | Red (coral) | Job is experiencing labour cost overruns |
| **Ongoing** | Green | Job is in progress, healthy status |

### 2.5 Pagination

```
Rows per page: [50 ▼]   Page 1 of 2   [«] [<] [>] [»]   Go to page: [1] of 2
```

- First page (<<), Previous (<), Next (>), Last (>>) buttons
- Direct page number input

---

## 3. Job Detail View — Summary Tab

### 3.1 Job Context Bar

```
┌─────────────────────────────────────────────────────────────────────────┐
│ Job: #J5955  │  Site: DPK 4705 - Bulleen Zones 2 & 3 Roof  │           │
│              │  Client: SPARK Consortium                     │           │
│              │  Project Manager: PU SUP Uriah Gray           │  🔔 👤 ☀️ │
└─────────────────────────────────────────────────────────────────────────┘
```

Always visible at top of job detail pages.

### 3.2 Breadcrumb Navigation

```
Active-jobs > 5955
← Back to Active Jobs page
```

### 3.3 Tab Navigation

| Tab | Purpose | Style |
|-----|---------|-------|
| **Summary** | Overall job overview | Default/active |
| **Labour** | Labour hours, costs, analysis | Standard tab |
| **Materials** | Material costs and tracking | Standard tab |
| **Equipment** | Equipment costs and tracking | Standard tab |
| **Subcontractors** | Subcontractor costs | Standard tab |
| **Others** | Miscellaneous costs | Standard tab |
| **Quote Sheet** | Original quote breakdown | Outlined/emphasis |
| **Note** | Job notes and comments | Outlined/emphasis |

### 3.4 Summary Tab Layout

```
┌─────────────────────────────────────────────────────────────────────────┐
│ ┌─────────────────┐  ┌───────────────────┐  ┌─────────────────────────┐ │
│ │   Job Details   │  │  Contract Value   │  │     Cost Control        │ │
│ └─────────────────┘  └───────────────────┘  └─────────────────────────┘ │
│                                                                          │
│ ┌─────────────────────────────────┐  ┌──────────────────────────────┐  │
│ │   Project Financial Budgets     │  │     Budget vs Actual         │  │
│ └─────────────────────────────────┘  └──────────────────────────────┘  │
└─────────────────────────────────────────────────────────────────────────┘
```

#### 3.4.1 Job Details Card

| Field | Example Value | Notes |
|-------|---------------|-------|
| **Client** | SPARK Consortium | Client company name |
| **Job Address** | DPK 4705 - Bulleen Zones 2 & 3 Roof | Site location |
| **Estimator** | E Lance Donald | Original estimator |
| **Project Manager** | PU SUP Uriah Gray | Current PM |
| **Job Start Date** | 22 Aug 24 | Project commencement |
| **Date of Last Invoice** | 22 Oct 25 | Most recent billing |
| **Labour Cost Rate** | $124 | Hourly labour cost rate |

#### 3.4.2 Contract Value Card

| Field | Value | Percentage |
|-------|-------|------------|
| **Original Contract Value** | $2,166,402 | 99.99% (base reference) |
| **Approved Variations** | $541,983 | 20.01% |
| **Revised Contract Value** | $2,708,385 | 100.00% |
| **Invoiced to Date** | $1,222,578 | 15.14% |
| **Balance to Invoice** | $1,485,806 | 4.86% |

#### 3.4.3 Job Hours Section

| Field | Value | Percentage |
|-------|-------|------------|
| **Original Contract** | 3443.53H | 69.27% |
| **Approved Variations** | 1527.40H | 36.73% |

#### 3.4.4 Cost Control Section

**Receivables:**
| Metric | Value |
|--------|-------|
| Invoiced to Date | $1,222,578 |
| Received to Date | $1,034,495 |
| Balance Owing | $188,083 |

**Payables (by Category):**
| Category | Total Budget | Invoices Rec'd to Date |
|----------|--------------|------------------------|
| Labour | $621,783 | $577,517 |
| Materials | $1,077,585 | $406,610 |
| Equipment | $1,000 | $811 |
| Subcontractor | $27,959 | $38,752 |
| Others | $21,876 | - |
| **Total** | **$1,750,203** | **$1,023,690** |

#### 3.4.5 Budget vs Actual Section

```
Completion Progress (%): 45.14%    [AI Insights ✨]
```

---

## 4. Job Detail View — Labour Tab

### 4.1 Tab Layout

```
┌─────────────────────────────────────────────────────────────────────────┐
│ ┌─────────────────────┐  ┌─────────────────────┐  ┌──────────────────┐ │
│ │  Contract Details   │  │  Budget vs Actual   │  │ FORECAST at      │ │
│ │                     │  │                     │  │ Completion       │ │
│ └─────────────────────┘  └─────────────────────┘  └──────────────────┘ │
│                                                                          │
│ ┌─────────────────────────────────────────────────────────────────────┐ │
│ │                        Labour Table                    [⊝ Hide]    │ │
│ └─────────────────────────────────────────────────────────────────────┘ │
│                                                                          │
│ ┌─────────────────────────────────────────────────────────────────────┐ │
│ │                       Labour Analysis                  [⊝ Hide]    │ │
│ └─────────────────────────────────────────────────────────────────────┘ │
└─────────────────────────────────────────────────────────────────────────┘
```

### 4.2 Contract Details Section

**Labour Rates:**
| Field | Value |
|-------|-------|
| Labour Cost Rate | $124 |
| Labour C/O Rate | $201 |

**Labour Hours:**
| Field | Value |
|-------|-------|
| Total Budget | 4970.93H |

**Labour Gross Margin:**
| Field | Value |
|-------|-------|
| C/O Income | $1,056,762 |
| Expenses | $621,783 |
| Gross Margin | $434,979 |

### 4.3 Budget vs Actual Section

```
Completion Progress (%): 45.1%
```

| Metric | Budget to Date (45.14%) | Actual to Date (88.72%) | Variance (-43.58%) |
|--------|-------------------------|-------------------------|---------------------|
| **Labour Revenue** | $477,022 | $937,588 | $(460,566) |
| **Labour Cost** | $280,673 | $577,517 | $(296,844) |
| **Labour Gross Margin** | $196,349 | $360,071 | $(163,722) |
| **Labour Hours** | 2243.88H | 4676.25H | 2432.37H |

**Labour Hours Remaining:** 295H
```
[████████████████████████████████████░░░░░░░░░░░░░░░░░░░░░░] 295H remaining
```

### 4.4 Forecast at Completion Section

| Metric | Current Trend |
|--------|---------------|
| Completion Forecast | $1,056,762 |
| (Labour Cost Forecast) | $1,279,391 |
| (Labour Hours Forecast) | 10359.44H |

### 4.5 Labour Table Section

**Filter:** `🔽 Select Months ▼`

**Toggle:** `[⊝ Hide]` button to collapse section

| Metric | Total | Last Month (Dec 25) | Prior Month 1 (Oct 25) | Prior Month 2 (Aug 25) | ... |
|--------|-------|---------------------|------------------------|------------------------|-----|
| **Hours (H)** | 4676.25 | - | 153.00 | 125.50 | 106 |
| **Labour Revenue (Target) ($)** | 937,588 | - | 30,677 | 25,163 | 214 |
| **Labour Cost ($)** | 577,517 | - | 18,896 | 15,499 | 13 |
| **Labour Gross Margin ($)** | 360,071 | - | 11,781 | 9,664 | 82 |

Visual progress bar indicator below table.

### 4.6 Labour Analysis Section

**Filter:** `🔽 Monthly ▼`

**Toggle:** `[⊝ Hide]` / `[↺ Unhide]` button

| Metric | ℹ️ | Total | Month 1 (Jan 24) | Month 2 (May 24) | Month 3 (Jun 24) | Month 4 (Aug 24) |
|--------|---|-------|------------------|------------------|------------------|------------------|
| **Target Forecast of Invoice ($)** | ℹ️ | 2,564,749 | 0 | 11,381 | 137 | 164,265 |
| **Invoicing Total ($)** | ℹ️ | 1,222,578 | 0 | 0 | 0 | 79,167 |
| **Gross Margin on Labour Cost ($)** | ℹ️ | 645,062 | 0 | (2,563) | (31) | 42,178 |
| **Margin leftover in Invoice (%)** | ℹ️ | 53 | 0 | 0 | 0 | 53 |
| | | | | | | |
| **Actual Labour Revenue ($)** | ℹ️ | 477,028 | 0 | 0 | 0 | 30,889 |
| **Actual Labour Cost ($)** | ℹ️ | (577,517) | 0 | (2,563) | (31) | (36,988) |
| **Budgeted Labour Cost ($)** | ℹ️ | (275,294) | 0 | 0 | 0 | (17,826) |
| **Earned Value ($)** | ℹ️ | (302,223) | 0 | (2,563) | (31) | (19,162) |
| **Gross Profit Attributable to Labour ($)** | ℹ️ | (100,489) | 0 | (2,563) | (31) | (6,099) |
| **Labour Profit Margin (%)** | ℹ️ | (21.1) | 0.0 | 0.0 | 0.0 | (18.7) |

**Color Coding:**
- Red values in parentheses indicate negative/loss figures
- Standard black for positive values

---

## 5. Job Detail View — Materials Tab

### 5.1 Materials Tab Layout

Follows the same three-section pattern as Labour tab.

### 5.2 Contract Details Section

**Materials Gross Margin:**
| Field | Value | Percentage |
|-------|-------|------------|
| Charge Out Value | $1,514,432 | - |
| Cost Value | $1,077,585 | 0.00% |
| Gross Margin | $436,847 | 28.85% |
| Completion Progress (%) | 45.14% | - |
| Remaining Budget | $670,975 | - |

### 5.3 Budget vs Actual Section

| Metric | Budget to Date (45.14%) | Actual to Date (37.73%) | Variance (7.41%) |
|--------|-------------------------|-------------------------|------------------|
| **Materials Revenue** | $683,615 | $571,447 | $197,193 |
| **Materials Cost** | $486,422 | $406,610 | $79,812 |
| **Materials Gross Margin** | $197,193 | $164,837 | $32,355 |

### 5.4 Materials Table

**Filter:** `🔽 Select Months ▼`

| Metric | Total | Last Month (Oct 25) | Prior Month 1 (Aug 25) | Prior Month 2 (Jul 25) |
|--------|-------|---------------------|------------------------|------------------------|
| Materials Charge Out Revenue (Target) ($) | 665,138 | 665,138 | - | - |
| Materials Cost Value ($) | 406,610 | 535 | 34 | 74,844 |
| Materials Gross Margin ($) | 664,603 | 664,603 | - | - |

### 5.5 Materials Analysis Section

**Filter:** `🔽 Monthly ▼`

| Metric | ℹ️ | Total | Month 1 | Month 2 | Month 3 | Month 4 |
|--------|---|-------|---------|---------|---------|---------|
| **Invoices Raised ($)** | ℹ️ | 1,222,578 | 0 | 0 | 0 | 79,167 |
| **Bills with Project ($)** | ℹ️ | (406,610) | (698) | (754) | 0 | (30,386) |
| **Materials Margin ($)** | ℹ️ | 815,968 | (698) | (754) | 0 | 48,781 |
| **Margin (%)** | ℹ️ | 67 | 0 | 0 | 0 | 62 |
| **Material Margin Target ($)** | ℹ️ | 894,316 | 0 | 0 | 0 | 57,910 |
| **Over/Under Margin Target (%)** | ℹ️ | (9) | 0 | 0 | 0 | (16) |

---

## 6. Job Detail View — Equipment Tab

### 6.1 Contract Details Section

**Equipment Gross Margin:**
| Field | Value | Percentage |
|-------|-------|------------|
| Charge Out Value | $1,350 | - |
| Cost Value | $1,000 | 74.07% |
| Gross Margin | $350 | 25.93% |
| Completion Progress (%) | 45.14% | - |
| Remaining Budget | $189 | - |

### 6.2 Budget vs Actual Section

| Metric | Budget to Date (45.14%) | Actual to Date (81.14%) | Variance (-36.00%) |
|--------|-------------------------|-------------------------|---------------------|
| **Equipment Revenue** | $609 | $1,095 | $158 |
| **Equipment Cost** | $451 | - | - |
| **Equipment Gross Margin** | $158 | $284 | $(126) |

### 6.3 Equipment Table

| Metric | Total | Last Month (Oct 25) | Prior Month 1 (Aug 25) | Prior Month 2 (Jul 25) |
|--------|-------|---------------------|------------------------|------------------------|
| Equipment Charge Out Revenue (Target) ($) | 593 | 593 | - | - |
| Equipment Cost Value ($) | 811 | 142 | 339 | 331 |
| Equipment Gross Margin ($) | 451 | 451 | - | - |

### 6.4 Equipment Analysis Section

| Metric | ℹ️ | Total | Month 1 | Month 2 | Month 3 | Month 4 |
|--------|---|-------|---------|---------|---------|---------|
| **Invoices Raised ($)** | ℹ️ | 1,222,578 | 0 | 0 | 0 | 79,167 |
| **Bills with Project ($)** | ℹ️ | (811) | 0 | 0 | 0 | 0 |
| **Equipment Margin ($)** | ℹ️ | 1,221,767 | 0 | 0 | 0 | 79,167 |
| **Margin (%)** | ℹ️ | 100 | 0 | 0 | 0 | 100 |
| **Equipment Margin Target ($)** | ℹ️ | 487,809 | 0 | 0 | 0 | 31,587 |
| **Over/Under Margin Target (%)** | ℹ️ | 150 | 0 | 0 | 0 | 151 |

---

## 7. Job Detail View — Subcontractors Tab

### 7.1 Contract Details Section

**Subcontractor Gross Margin:**
| Field | Value | Percentage |
|-------|-------|------------|
| Charge Out Value | $37,816 | - |
| Cost Value | $27,959 | 73.94% |
| Gross Margin | $9,857 | 26.06% |
| Completion Progress (%) | 45.14% | - |
| Remaining Budget | $(10,792) | ⚠️ **Negative** (over budget) |

### 7.2 Budget vs Actual Section

| Metric | Budget to Date (45.14%) | Actual to Date (-) | Variance (-) |
|--------|-------------------------|--------------------|--------------|
| **Subcontractor Revenue** | $17,070 | $52,413 | $4,449 |
| **Subcontractor Cost** | $12,621 | $38,752 | $(26,131) |
| **Subcontractor Gross Margin** | $4,449 | $13,661 | $(9,212) |

### 7.3 Subcontractor Table

| Metric | Total | Last Month (Oct 25) | Prior Month 1 (Aug 25) | Prior Month 2 (Jul 25) |
|--------|-------|---------------------|------------------------|------------------------|
| Subcontractor Charge Out Revenue (Target) ($) | 16,609 | 16,609 | - | - |

### 7.4 Subcontractor Analysis Section

| Metric | ℹ️ | Total | Month 1 | Month 2 | Month 3 | Month 4 |
|--------|---|-------|---------|---------|---------|---------|
| **Invoices Raised ($)** | ℹ️ | 1,222,578 | 0 | 0 | 0 | 79,167 |
| **Bills with Project ($)** | ℹ️ | (38,752) | 0 | 0 | 0 | 0 |
| **Subcontractor Margin ($)** | ℹ️ | 1,183,827 | 0 | 0 | 0 | 79,167 |
| **Margin (%)** | ℹ️ | 97 | 0 | 0 | 0 | 100 |
| **Subcontractor Margin Target ($)** | ℹ️ | (24,452) | 0 | 0 | 0 | (1,583) |
| **Over/Under Margin Target (%)** | ℹ️ | (4,942) | 0 | 0 | 0 | (5,100) |

---

## 8. Job Detail View — Others Tab

### 8.1 Contract Details Section

**Others Gross Margin:**
| Field | Value | Percentage | Status |
|-------|-------|------------|--------|
| Charge Out Value | $19,107 | - | - |
| Cost Value | $21,876 | 114.49% | ⚠️ Over budget |
| Gross Margin | $(2,769) | -14.49% | 🔴 **Negative margin** |
| Completion Progress (%) | 45.14% | - | - |
| Remaining Budget | $21,876 | - | - |

### 8.2 Budget vs Actual Section

| Metric | Budget to Date (45.14%) | Actual to Date (-) | Variance (45.14%) |
|--------|-------------------------|--------------------|-------------------|
| **Others Revenue** | $8,625 | - | $(1,250) |
| **Others Cost** | $9,875 | - | $9,875 |
| **Others Gross Margin** | $(1,250) | - | $(1,250) |

### 8.3 Others Table

```
No monthly data available.
```

### 8.4 Others Analysis Section

| Metric | ℹ️ | Total | Month 1 | Month 2 | Month 3 | Month 4 | Month 5 | Month 6 |
|--------|---|-------|---------|---------|---------|---------|---------|---------|
| **Invoices Raised ($)** | ℹ️ | 1,222,578 | 0 | 0 | 0 | 79,167 | 118,468 | 35,796 |
| **Others Bills with Project ($)** | ℹ️ | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| **Others Margin ($)** | ℹ️ | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| **Margin (%)** | ℹ️ | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| **Others Margin Target ($)** | ℹ️ | 894,316 | 0 | 0 | 0 | 79,167 | 118,468 | 35,796 |
| **Over/Under Margin Target (%)** | ℹ️ | 0 | 0 | 0 | 0 | 0 | 0 | 0 |

---

## 9. Job Detail View — Quote Sheet Tab

### 9.1 Quote Sheet Layout

```
┌─────────────────────────────────────────────────────────────────────────┐
│ ┌───────────────┐  ┌───────────────┐  ┌───────────────┐  ┌───────────┐ │
│ │  Job Details  │  │Contract Value │  │Contract Labour│  │   Gross   │ │
│ │               │  │               │  │    Rates      │  │  Margins  │ │
│ └───────────────┘  └───────────────┘  └───────────────┘  └───────────┘ │
│                                                                          │
│ ┌────────────────────────────────────────────────────────────────────┐  │
│ │                QUOTE / VARIATION TABLE                              │  │
│ │  [+ Upload Quote]                                                   │  │
│ └────────────────────────────────────────────────────────────────────┘  │
│                                                                          │
│ ┌────────────────────────────────────────────────────────────────────┐  │
│ │                         NOTES SECTION                              │  │
│ └────────────────────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────────────────┘
```

### 9.2 Header Cards

**Job Details Card:**
| Field | Value |
|-------|-------|
| Client | SPARK Consortium |
| Job Address | DPK 4705 - Bulleen Zones 2 & 3 Roof |
| Estimator | E Lance Donald |
| Project Manager | PU SUP Uriah Gray |
| Job Start Date | 22 Aug 24 |
| Date of Last Invoice | 22 Oct 25 |

**Contract Value Card:**
| Field | Value | Percentage |
|-------|-------|------------|
| Original Contract Value | $2,166,402 | 79.99% |
| Approved Variations | $541,983 | 20.01% |
| Revised Contract Value | $2,708,385 | - |

**Job Hours Card:**
| Field | Value | Percentage |
|-------|-------|------------|
| Original Contract | 3443.53H | 69.27% |
| Approved Variations | 1527.40H | 30.73% |

**Contract Labour Rates:**
| Field | Value |
|-------|-------|
| Labour Cost Rate | $124 |
| Labour C/O Rate | $201 |

**Gross Margins:**
| Field | Value | Percentage |
|-------|-------|------------|
| Contract Totals | $686,063 | 31.67% |
| Contract & Variation Totals | $958,181 | 35.38% |

### 9.3 Quote/Variation Table Structure

**Table Columns:**
| Column | Description |
|--------|-------------|
| Quote Number | Identifier (e.g., Q9275R45, VAR001_Q10065R3_CombiFlex) |
| Approval Status | ✓ (approved) / ✕ (rejected) icons for Charge Out Values and Budget/KPI Values |
| Man hour | Total hours for quote/variation |
| Labour rates | Rate applied |
| Quote / Variation | Dollar value |

**Row Types:**
1. **Contract Quote** — Original contract (expandable)
2. **Variation 1, 2, 3...** — Individual variations (expandable)
3. **TOTAL Contract & Charge Out Values** — Sum row
4. **TOTAL BUDGET / KPI Values** — Sum row

### 9.4 Quote Line Items (Expanded View)

When a quote row is expanded, shows line item details:

| Column | Description |
|--------|-------------|
| Item | Line number (1, 2, 3...) |
| Description | "Supply and install..." with [Show more] link |
| Product/System | Product name (e.g., "Fosroc A900 5mm", "Sika Monotop 723") |
| Work Area | Square meters or units (e.g., 16,855 / 444 / 341) |
| CTC Labour | Cost to complete labour ($) |
| Rev Labour | Revenue labour ($) |
| CTC Product | Cost to complete product ($) |
| Rev Product | Revenue product ($) |
| Total Revenue | Combined revenue ($) |
| Est Labour D[ays] | Estimated labour days |

### 9.5 Example Quote Line Items

**Contract Quote (Q9275R45) Expanded:**

| Item | Description | Product/System | Work Area | CTC Labour | Rev Labour | CTC Product | Rev Product | Total Revenue | Est Labour |
|------|-------------|----------------|-----------|------------|------------|-------------|-------------|---------------|------------|
| 1 | Supply and install... | Fosroc A900 5mm | 16,855 | $133,221 | $216,283 | $34 | $811,914 | $887,086.00 | 134 |
| 2 | Supply and install... | Fosroc A900 5mm | 444 | $10,966 | $17,804 | $19 | $12,017 | $27,001.00 | 11 |
| 3 | Supply and install... | Generic Pressure Bar | 444 | $10,966 | $17,804 | $6 | $3,874 | $21,680.00 | 11 |
| 4 | Supply and install... | Sika Monotop 723 | 341 | $11,230 | $18,232 | $4 | $2,188 | $20,420.00 | 11 |
| 5 | Supply and install... | Fosroc A700 4mm | 853 | $42,138 | - | - | - | - | - |
| 6 | Supply and install... | Generic Pressure Bar | 341 | $8,422 | - | - | - | - | - |
| 7 | Supply and install... | Fosroc Sheetdrain | 853 | $8,427 | - | - | - | - | - |
| 8 | Commission and coordinate... | ILD Australia | 17,685 | $0 | - | - | - | - | - |

### 9.6 Variations List

| Variation | Quote Number | Man Hours | Labour Rate | Value |
|-----------|--------------|-----------|-------------|-------|
| Contract Quote | Q9275R45 | 3443.53H | $201 / $124 | $2,166,402 |
| Variation 1 | Escalation | 0.00H | $0 / $0 | $84,961 |
| Variation 2 | VAR001_Q10065R3_CombiFlex | 434.40H | $235 / $130 | $107,571 |
| Variation 3 | NightWorksMay2025_Q10216R1 | 64.00H | $210 / $95 | $9,760 |
| Variation 4 | DayWorksMay2025_Q10239 | 37.00H | $210 / $135 | $9,538 |
| Variation 5 | VAR003_Q10270R1_DWall | 992.00H | $245 / $130 | $330,153 |
| Variation 8 | 5955_12_daysheet | 0.00H | $0 / $0 | $0 |

**Totals:**
| Total Type | Man Hours | Value |
|------------|-----------|-------|
| TOTAL Contract & Charge Out Values | - | $2,708,385 |
| TOTAL BUDGET / KPI Values | 4970.93H | - |

---

## 10. AI Insights Side Panel

### 10.1 Panel Structure

The AI Insights button opens a **slide-out side panel** with four tabs:

```
┌────────────────────────────────────────────────────────────────────────┐
│  [AI Insights]  [Notes]  [Files]  [Settings]              [↻ Update]  │
├────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│  ▼ Summary                                                              │
│  ┌─────────────────────────────────────────────────────────────────┐   │
│  │ ⊙ Collect BR21964 >90d                                          │   │
│  │ ⊙ Lift labour realisation on remaining hours                    │   │
│  │ ⊙ Recover October labour gap via variation                      │   │
│  │ ⊙ Labour realisation 30.6% below rate; EV -121.5k              │   │
│  │ ⊙ AR >90 188.1k; urgent collection required.                    │   │
│  │ ⊙ Materials 671.5k under budget; sustain procurement controls.  │   │
│  └─────────────────────────────────────────────────────────────────┘   │
│                                                                         │
│  ▼ Labour                                                               │
│  └ (collapsed)                                                          │
│                                                                         │
│  ▼ Materials                                                            │
│  └ (collapsed)                                                          │
│                                                                         │
│  ▼ Equipment                                                            │
│  └ (collapsed)                                                          │
│                                                                         │
│  ▼ Subcontractors                                                       │
│  └ (collapsed)                                                          │
│                                                                         │
│  ▼ Others                                                               │
│  └ (collapsed)                                                          │
│                                                                         │
└────────────────────────────────────────────────────────────────────────┘
```

### 10.2 AI Insights Tab

**Purpose:** AI-generated actionable insights organized by cost category

**Insight Categories:**
- Summary (expanded by default)
- Labour
- Materials
- Equipment
- Subcontractors
- Others

**Example Summary Insights:**
| Insight | Type |
|---------|------|
| Collect BR21964 >90d | Collections/AR |
| Lift labour realisation on remaining hours | Labour efficiency |
| Recover October labour gap via variation | Variation opportunity |
| Labour realisation 30.6% below rate; EV -121.5k | Performance warning |
| AR >90 188.1k; urgent collection required | Cash flow alert |
| Materials 671.5k under budget; sustain procurement controls | Positive performance |

**Update Button:** `[↻ Update]` — Refreshes AI analysis

### 10.3 Notes Tab

**Structure:**
```
┌────────────────────────────────────────────────────────────────────────┐
│  Notes                                                        [Saved]  │
├────────────────────────────────────────────────────────────────────────┤
│  ┌─────────────────────────────────────────────────────────────────┐   │
│  │ Write a note... Type @ to mention                          📎   │   │
│  │                                                                  │   │
│  │                                                                  │   │
│  └─────────────────────────────────────────────────────────────────┘   │
│                                                                         │
│  by Siddhant Shukla                                                    │
│                                                                         │
│  No notes yet.                                                          │
│                                                                         │
└────────────────────────────────────────────────────────────────────────┘
```

**Features:**
- Rich text input area
- @ mentions for team members
- File attachment (📎)
- Auto-save indicator ("Saved")
- Author attribution
- Empty state: "No notes yet."

### 10.4 Files Tab

**Structure:**
```
┌────────────────────────────────────────────────────────────────────────┐
│  Invoices                                               4 files   ▼    │
│  ├─ 📄 BR22112.pdf                                    👁️   ⬇️         │
│  ├─ 📄 BR22074.pdf                                    👁️   ⬇️         │
│  ├─ 📄 BR22029.pdf                                    👁️   ⬇️         │
│  └─ 📄 BR21997.pdf                                    👁️   ⬇️         │
├────────────────────────────────────────────────────────────────────────┤
│  Bills                                                 38 files   ▶    │
├────────────────────────────────────────────────────────────────────────┤
│  Quotes & Variations                                    3 files   ▶    │
└────────────────────────────────────────────────────────────────────────┘
```

**File Categories:**
| Category | Count | Description |
|----------|-------|-------------|
| Invoices | 4 files | Invoice PDFs (BR#####.pdf) |
| Bills | 38 files | Supplier bills |
| Quotes & Variations | 3 files | Quote documents |

**File Actions:**
- 👁️ Preview/View
- ⬇️ Download

### 10.5 Settings Tab

**Team Management:**
```
┌────────────────────────────────────────────────────────────────────────┐
│  Team                                                       [+ Invite] │
│  Manage workspace members                                              │
├────────────────────────────────────────────────────────────────────────┤
│  🔍 Search team members...                                             │
├────────────────────────────────────────────────────────────────────────┤
│  [LV] Luc Volschenk                           📞 0468828389            │
│       luc.volschenk@bravada.com.au                                     │
│                                                                         │
│  [👤] Vibhuti Rajpal                          📞 123                    │
│       vibhuti@finsoeasy.com                                            │
│                                                                         │
│  [RG] Rashi Gupta                                                       │
│       rashi.gupta@finsoeasy.com                                        │
│                                                                         │
│  [AS] Abhishek Sehgal                                                   │
│       abhishek@finsoeasy.com                                           │
│                                                                         │
│  [👤] Sohali Chatterjee                                                 │
│       sohali.chatterjee@finsoeasy.com                                  │
│                                                                         │
│  [SP] Sayoni Pandit                                                     │
│       sayoni.pandit@finsoeasy.com                                      │
│                                                                         │
│  [AG] Aditi Garg                                                        │
│       aditi.garg@finsoeasy.com                                         │
└────────────────────────────────────────────────────────────────────────┘
```

**Features:**
- Search team members
- Invite new members
- Display: Avatar/Initials, Name, Email, Phone (optional)

---

## 11. Summary Dashboard (Additional View)

### 11.1 Cost Category Breakdown Table

**Charge Out vs Cost Comparison:**

| Category | Charge Out | % | Cost | % | Gross Margin | % |
|----------|------------|---|------|---|--------------|---|
| Labour | $1,056,762 | 40.21% | $621,783 | 35.49% | - | - |
| Materials | $1,514,432 | 57.59% | $1,077,585 | 61.57% | $436,847 | 49.68% |
| Equipment | $1,350 | 0.05% | $1,000 | 0.06% | $350 | 0.04% |
| Contract Services | $37,816 | 1.44% | $27,959 | 1.60% | $9,857 | 1.12% |
| Other | $19,107 | 0.73% | $21,876 | 1.25% | $(2,769) | -0.31% |
| **Total** | **$2,629,467** | **100.00%** | **$1,750,203** | **124.85%** | **$879,263** | **100.00%** |
| % Share | 100.00% | | 66.56% | | 33.44% | |

### 11.2 Budget vs Actual Summary

| Category | Budget | % Completion | Actual | % | Variance |
|----------|--------|--------------|--------|---|----------|
| Labour | $280,673 | 45.14% | $577,517 | 92.88% | $(296,844) |
| Materials | $486,422 | 45.14% | $406,610 | 37.73% | $79,812 |
| Equipment | $451 | 45.14% | $811 | 81.14% | $(360) |
| Contract Services | $12,621 | 45.14% | $38,752 | 138.60% | $(26,131) |
| Other | $9,875 | 45.14% | - | 0.00% | $9,875 |
| **Total** | **$790,042** | **45.14%** | **$1,023,690** | **129.57%** | **$(233,648)** |
| Labour Hours | 2243.88H | | 4676.25H | | 2432.37H |

### 11.3 User Details Grid

Displays team members assigned to job with avatar grid:

```
┌───────────────────────────────────────────────────────────────────┐
│                        User Details                                │
├───────────────────────────────────────────────────────────────────┤
│  [LV]           [👤]           [RG]                               │
│  Luc Volschenk  Vibhuti Rajpal Rashi Gupta                       │
│  luc.volschenk  vibhuti@       rashi.gupta@                       │
│  @bravada...    finsoeasy.com  finsoeasy.com                      │
│                                                                    │
│  [AS]           [👤]           [SP]                               │
│  Abhishek       Sohali         Sayoni Pandit                      │
│  Sehgal         Chatterjee     sayoni.pandit@                     │
│  abhishek@...   sohali...      finsoeasy.com                      │
│                                                                    │
│  [AG]           [LD]           [SB]                               │
│  Aditi Garg     Lance Donald   Steve Baker                        │
│  aditi.garg@... lance.donald@  steve.baker@                       │
│                 bravada...     bravada.com.au                      │
└───────────────────────────────────────────────────────────────────┘
```

---

## 12. Notes Section (All Tabs)

### 12.1 Notes Table Structure

Present at the bottom of most tabs:

| Column | Description |
|--------|-------------|
| Description | Note content |
| Created By | Author name |
| Time | Timestamp |
| Files | Attached files |
| Actions | Edit/Delete |

**Actions:**
- `[⊝ Hide]` — Collapse section
- `[+ Add]` — Add new note

**Empty State:** "No notes"

---

## 14. All Quotations Module

### 14.1 Page Header & Search

```
Page Title: "All Quotations"

┌─────────────────────────────────────────────────────────────────────────┐
│  🔍 Search quote...                    [Advanced Search]     [⬇️ Export] │
└─────────────────────────────────────────────────────────────────────────┘
```

### 14.2 Filter Bar

| Filter | Type | Options |
|--------|------|---------|
| **Project Manager** | Dropdown | Search manager |
| **Sales Person** | Dropdown | Search sales |
| **Client** | Dropdown | Search client |
| **Status** | Dropdown | Select Status |
| **Site** | Dropdown | Search site |
| **Priority** | Dropdown | Select Priority |

Each filter has a `[Clear]` link to reset.

### 14.3 Quote Status Tabs

| Tab | Description |
|-----|-------------|
| **All quotes** | All quotes regardless of status |
| **Active** | Quotes currently being worked on |
| **Archive** | Archived/completed quotes |

### 14.4 Quote Card Structure (Create New)

```
┌─────────────────────────────────────────────────────────────────────────┐
│  Title: [Enter title]          Sales person: [🔍 Search]               │
│  ████ (color bar)              Project manager: [🔍 Search]    [+ Tag] │
│                                                         [Pending ▼]    │
│                                                    [Save Quote] [✕]    │
├─────────────────────────────────────────────────────────────────────────┤
│  Client: [🔍 Search] [Create New]    Site: [🔍 Search] [Create New]    │
│                                                                         │
│  Client Contact: [🔍 Select client first]                               │
│  [Create New]                         Email: [email@example.com]        │
│                                       Phone: [Enter phone]              │
│                                       Position: [Enter position]        │
│                                                                         │
│  Date Chased: [dd/mm/yyyy 📅]         Due Date: [dd/mm/yyyy 📅]        │
│                                                                         │
│  Estimate Value: [0]                  Quote Received: [dd/mm/yyyy 📅]   │
│  Win Rate: [Select rate ▼]            Submitted Date: [dd/mm/yyyy 📅]   │
├─────────────────────────────────────────────────────────────────────────┤
│  [Enter a note...]                                                      │
├─────────────────────────────────────────────────────────────────────────┤
│  Quote submitted                                                    ⬆️  │
│  Selected file will be uploaded when you save this quotation.          │
│  No quote files uploaded yet.                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 14.5 Quote Card Fields

| Field | Type | Description |
|-------|------|-------------|
| **Title** | Text input | Quote identifier (e.g., "Q17 - TestQuote") |
| **Color Bar** | Color selector | Visual categorization (green, yellow, orange, etc.) |
| **Sales person** | Search/Select | Assigned salesperson |
| **Project manager** | Search/Select | Assigned PM |
| **Tag** | Button | Add tags |
| **Status** | Dropdown | Pending, Archive, etc. |
| **Client** | Search/Select + Create New | Client company |
| **Site** | Search/Select + Create New | Project site |
| **Client Contact** | Search/Select + Create New | Contact person |
| **Email** | Email input | Contact email |
| **Phone** | Phone input | Contact phone |
| **Position** | Text input | Contact's job title |
| **Date Chased** | Date picker | Last follow-up date |
| **Due Date** | Date picker | Quote deadline |
| **Estimate Value** | Currency | Estimated quote value |
| **Win Rate** | Dropdown | Probability percentage (0%, etc.) |
| **Quote Received** | Date picker | Date quote was received |
| **Submitted Date** | Date picker | Date quote was submitted |
| **Note** | Text area | Free-form notes with @ mentions |
| **Quote submitted** | File upload | Attach quote documents |

### 14.6 Quote Card (Saved/View Mode)

```
┌─────────────────────────────────────────────────────────────────────────┐
│ Q17 - TestQuote    Sales person: Kishan Antony                          │
│ ████████           Project manager: Tim McMahon          [Archive ▼]    │
│                                                           [✏️] [⋮]      │
├─────────────────────────────────────────────────────────────────────────┤
│  Client: Example-Client              Site: Kids Time Early Learning     │
│  Client Contact: Example Contact     Estimate Value: 25,000             │
│  Email: example-contact@123.com      Win Rate: 0%                       │
│  Phone: 1234                         Position: Administration           │
│  Date Chased: -                      Quote Received: -                  │
│  Due Date: -                         Submitted Date: -                  │
├─────────────────────────────────────────────────────────────────────────┤
│  [Enter a note...]                                                      │
│  ┌─────────────────────────────────────────────────────────────────┐   │
│  │ @Sayoni Pandit test @Sohali Chatterjee                          │   │
│  │                               by Siddhant Shukla  9 Oct, 10:08 pm│   │
│  │                                                         🗑️  ⌄   │   │
│  └─────────────────────────────────────────────────────────────────┘   │
├─────────────────────────────────────────────────────────────────────────┤
│  Quote submitted                                                    ⬆️  │
│  No quote files uploaded yet.                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 14.7 Quote Actions Menu (⋮)

| Action | Description |
|--------|-------------|
| **Mark as quoted** | Update status to quoted |
| **Allocate to existing jobs** | Link quote to a job |
| **Copy** | Duplicate quote |
| **Delete** | Remove quote (red text) |

---

## 15. Reports Module

### 15.1 Reports Submenu

The Reports section expands to show:

| Report | Description |
|--------|-------------|
| **Job Performance Summary** | Overview of all jobs with key metrics |
| **Pro-rata Analysis** | Detailed budget vs actual pro-rated analysis |
| **Financial Report** | Monthly financial breakdown |
| **Man Hours** | Workforce capacity and utilization |
| **Chargeout Projection** | Revenue forecasting |

### 15.2 Common Report Controls

All reports share:

```
┌─────────────────────────────────────────────────────────────────────────┐
│  Status: [All ▼]  [Select Date Range]  Project Manager: [All ▼]        │
│  Page Size: [50 per page ▼]  [Report Type ▼]  🔍 Search...             │
├─────────────────────────────────────────────────────────────────────────┤
│  [< Prev] [Next >] [↺ Reset] [⊝ Hide (0)] [⬇️ Export]                  │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## 16. Job Performance Summary Report

### 16.1 Purpose

High-level overview of all jobs with contract values, invoicing status, WIP, and completion percentage.

### 16.2 Table Columns

| Column | Description | Example |
|--------|-------------|---------|
| ☐ | Row selector checkbox | - |
| **Job** | Job number | 5955, 6466, 6234 |
| **Client** | Client company name | SPARK Consortium |
| **Site** | Project location | DPK 4705 - Bulleen Zones 2 & 3 Roof |
| **Status** | Job status badge | Active Works (green), Bin |
| **Contract Value** | Total contract amount | $2,708,385 |
| **Invoice to Date** | Amount invoiced | $1,222,578 |
| **WIP** | Work in Progress value | $1,485,806 |
| **% Comp** | Completion percentage | 45.1% |

### 16.3 Sample Data

| Job | Client | Site | Status | Contract Value | Invoice to Date | WIP | % Comp |
|-----|--------|------|--------|----------------|-----------------|-----|--------|
| 5955 | SPARK Consortium | DPK 4705 - Bulleen Zones 2 & 3 Roof | Active Works | $2,708,385 | $1,222,578 | $1,485,806 | 45.1% |
| 6466 | North Western Program Alliance | Webster Street Level Crossing | Active Works | $1,326,102 | $152,537 | $1,173,564 | 11.5% |
| 6234 | SPARK Consortium | North Vent and Culvert | Active Works | $5,014,326 | $3,974,983 | $1,039,342 | 79.3% |
| 6499 | Delta Pty Ltd | MEL LA2 Data Centre | Active Works | $841,395 | $41,807 | $799,587 | 5.0% |
| 6387 | Built Pty Ltd | 140 William Street Melbourne | Active Works | $506,045 | $299,575 | $206,469 | 59.2% |
| 6253 | BRC Piling & Foundations | Waterside Hotel | Bin | $125,064 | $117,924 | $7,140 | 94.3% |

---

## 17. Pro-rata Analysis Report

### 17.1 Purpose

Comprehensive budget vs actual analysis with pro-rated calculations based on completion percentage. This is the most detailed financial report.

### 17.2 Table Columns (Full Width - Scrollable)

**Section 1: Job Identification**
| Column | Description |
|--------|-------------|
| ☐ | Row selector |
| **Job** | Job number |
| **Client Name** | Client company |
| **Site** | Project location |
| **Sales Person** | Original salesperson |
| **Project Manager** | Current PM |

**Section 2: Contract & Progress**
| Column | Description |
|--------|-------------|
| **Contract Value** | Total contract amount |
| **Invoicing to Date** | Amount invoiced |
| **% Completion** | Progress percentage |
| **Total Project Budget (Hours)** | Budgeted labour hours |

**Section 3: Labour Hours Analysis**
| Column | Description |
|--------|-------------|
| **Budgeted Hours – Pro Rata** | Hours budgeted for current completion % |
| **Actual Hours to Date** | Actual hours worked |
| **Variance – Pro Rata** | Hours variance (negative = over budget) |
| **Remaining Hours** | Hours left to complete |

**Section 4: Labour Cost Analysis**
| Column | Description |
|--------|-------------|
| **Labour Budget – Pro Rata $** | Labour cost budget pro-rated |
| **Actual Labour Cost to Date $** | Actual labour spend |
| **Variance $** | Labour cost variance |

**Section 5: Material Analysis**
| Column | Description |
|--------|-------------|
| **Material Budget – Pro Rata $** | Materials budget pro-rated |
| **Actual Material Cost to Date $'s** | Actual materials spend |
| **Material Variance $** | Materials variance |

**Section 6: Subcontractor Analysis**
| Column | Description |
|--------|-------------|
| **Subcontractor Budget – Pro Rata $'s** | Subcon budget pro-rated |
| **Actual Subcontractor Cost to Date $'s** | Actual subcon spend |
| **Subcontractor Variance $'s** | Subcon variance |

**Section 7: Equipment Analysis**
| Column | Description |
|--------|-------------|
| **Equipment Budget – Pro Rata $'s** | Equipment budget pro-rated |
| **Actual Equipment Cost to Date $'s** | Actual equipment spend |
| **Equipment Variance $'s** | Equipment variance |

**Section 8: Overall Analysis**
| Column | Description |
|--------|-------------|
| **Actual Spend to Date** | Total actual spend |
| **Remaining Budget to Complete** | Budget remaining |

### 17.3 Sample Pro-rata Data

| Job | Contract Value | % Completion | Budget Hours | Actual Hours | Variance Hours | Labour Budget $ | Actual Labour $ | Variance $ |
|-----|----------------|--------------|--------------|--------------|----------------|-----------------|-----------------|------------|
| 5955 | $2,708,385 | 53.4% | 4971H | 4676H | -2022H | $327,766 | $577,517 | -$249,750 |
| 6466 | $1,326,102 | 11.5% | 2457H | 131H | 152H | $38,146 | $17,685 | $20,461 |
| 6234 | $5,014,326 | 79.3% | 12950H | 19432H | -9158H | $1,376,650 | $2,603,821 | -$1,227,171 |

---

## 18. Financial Report

### 18.1 Purpose

Multi-month view of invoicing, costs, margins, and profitability by job.

### 18.2 Table Structure

**Fixed Columns:**
| Column | Description |
|--------|-------------|
| ☐ | Row selector |
| **Job** | Job number |
| **Customer** | Client name |
| **Site** | Project location |

**Monthly Columns (Repeated for each month):**

| Column Group | Columns | Description |
|--------------|---------|-------------|
| **Invoice (Ex GST)** | Oct 25, Nov 25, Dec 25... | Monthly invoicing amounts |
| **Labour Cost** | Oct 25, Nov 25, Dec 25... | Monthly labour costs |
| **Miscellaneous Cost** | Nov 25, Dec 25... | Other costs |
| **Total Cost** | Oct 25, Nov 25, Dec 25... | Combined monthly costs |
| **Gross Margin** | Oct 25, Nov 25, Dec 25... | Monthly gross margin |
| **Profit / Loss %** | Oct 25, Nov 25, Dec 25... | Monthly profit percentage |

### 18.3 Sample Financial Report Data

| Job | Customer | Site | Invoice Oct 25 | Invoice Nov 25 | Labour Oct 25 | Labour Nov 25 | Gross Margin Oct | Profit % Oct |
|-----|----------|------|----------------|----------------|---------------|---------------|------------------|--------------|
| J6499 | Delta Pty Ltd | MEL LA2 Data Centre | $20,563 | $21,244 | $7,502 | $6,988 | $5,591 | 27.2% |
| J6465 | Symal Infastructure | Point Cook Hospital | $14,872 | $40,115 | $4,784 | $4,085 | $504 | 3.4% |
| J6466 | North Western Program | Webster Street Level | $10,676 | $124,193 | $4,590 | $9,180 | $559 | 5.2% |
| J6431 | Blu line projects | 606-608 SOUTH ROAD | $20,952 | $0 | $5,249 | $340 | $14,713 | 70.2% |
| J6405 | Delta Pty Ltd | MEL LA1 | $4,238 | - | $12,044 | - | -$9,165 | -216.3% |
| J6387 | Built Pty Ltd | 140 William Street | $36,601 | $45,818 | $12,653 | $25,065 | $17,160 | 46.9% |

### 18.4 Color Coding

- **Red/Negative values**: Loss or negative variance (e.g., -28.8%, -216.3%)
- **Black/Positive**: Profit or positive results

---

## 19. Man Hours Report

### 19.1 Sub-Tabs

| Tab | Purpose |
|-----|---------|
| **Manpower Hours Build Up** | Employee capacity planning |
| **Calculate Man Hours** | Revenue and chargeout forecasting |
| **Calendar** | Calendar view of availability |

### 19.2 Manpower Hours Build Up

**Filters:**
- Year selector: [2025 ▼]
- Month selector: [November ▼]
- Daily Work Hours: [8]

**Actions:** [💾 Save] [✕ Cancel] [⬇️ Export]

**Table Columns:**

| Column | Type | Description |
|--------|------|-------------|
| **Onsite** | Checkbox | Worker is on-site |
| **Name** | Text | Employee name |
| **Employee Type** | Text | Permanent, Casual |
| **Classification** | Text | Operations, Supervisors, Non Union Casuals |
| **Union** | ✓/✕ | Union membership |
| **Basement** | ✓/✕ | Basement qualification |
| **Month** | Text | Current month |
| **Year** | Number | Current year |
| **Weekdays** | Number | Working weekdays in month |
| **Public Holidays** | Number | Public holidays |
| **RDO** | Number | Rostered days off |
| **Sick Leave** | Number | Sick leave days |
| **Annual Leave** | Number | Annual leave days |
| **Training** | Number | Training days |
| **Downtime Weather** | Number | Weather downtime |
| **Overtime** | Number | Overtime days |
| **Sub-Total Days** | Calculated | Net available days |
| **Tools Productivity (%)** | Number | Productivity factor (0-100) |
| **Total Available Work Days** | Calculated | Final available days |
| **Total Available Hours** | Calculated | Days × Daily hours |

### 19.3 Sample Manpower Data

| Name | Type | Classification | Union | Weekdays | PH | RDO | Sick | Sub-Total | Productivity | Avail Days | Avail Hours |
|------|------|----------------|-------|----------|-----|-----|------|-----------|--------------|------------|-------------|
| Steve Baker | Permanent | Operations | ✓ | 20 | 1 | 0 | 0.5 | 18.5 | 0 | 0.00 | 0.00 |
| Tim McMahon | Permanent | Operations | ✓ | 20 | 1 | 0 | 0.5 | 18.5 | 0 | 0.00 | 0.00 |
| Liam Millar | Casual | Non Union Casuals | ✓ | 20 | 1 | 0 | 0.5 | 17.5 | 100 | 17.50 | 140.00 |
| Albano Vuthi | Permanent | Supervisors | ✓ | 20 | 1 | 3 | 0.5 | 15.5 | 100 | 15.50 | 124.00 |

### 19.4 Calculate Man Hours Tab

**Section: Month Tracking & Revenue Analysis**

| Column | Description |
|--------|-------------|
| **Current** | Current month indicator |
| **Month Tracking** | Month/Year (Jul 2025, Aug 2025...) |
| **Enclosed Days** | Working days in period |
| **+/- target** | Variance from target (%) |
| **Actual Days Worked** | Actual working days |
| **Target Day** | Target working days |
| **Current Tracking Chargeout** | Current chargeout rate |
| **+/- Forecast \| Actual** | Forecast variance (%) |
| **End of Month Forecast Revenue** | Projected month-end revenue |
| **Actual Revenue** | Actual revenue achieved |
| **+/- Actual \| Planned** | Actual vs planned variance |
| **Planned Revenue** | Planned revenue |
| **Planned Days** | Planned working days |
| **Actual Chargeout Per Day** | Revenue per day |
| **Targeted Chargeout / Day** | Target revenue per day |
| **% of Month** | Month completion % |
| **Total Days in the Month** | Calendar days |
| **Man Hours Worked** | Actual hours |
| **Man Hours Targeted** | Target hours |

### 19.5 Sample Calculate Man Hours Data

| Month | Enclosed Days | +/- target | Actual Days | Chargeout | +/- Forecast | Forecast Revenue | Actual Revenue |
|-------|---------------|------------|-------------|-----------|--------------|------------------|----------------|
| Jul 2025 | 21.0 | 0.00% | 588.1 | $1,700 | -5.43% | $999,759 | $1,057,212 |
| Aug 2025 | 19.0 | 0.00% | 624.4 | $1,700 | -2.52% | $1,061,438 | $1,088,883 |
| Sep 2025 | 18.0 | 0.00% | 657.0 | $1,700 | -0.42% | $1,116,900 | $1,121,577 |
| Oct 2025 | 21.0 | 0.00% | 885.7 | $1,700 | 7.84% | $1,505,616 | $1,396,152 |
| Nov 2025 | 16.0 | 0.00% | 657.4 | $1,700 | -28.34% | $1,117,591 | $1,559,605 |
| Dec 2025 | 0.0 | 0.00% | 0.0 | $0 | 0.00% | $0 | $0 |

### 19.6 Month Sub Total - Available Work Days

Editable table for planning future months:

| Month | Sub Total Days | Weekdays | Public Holidays | RDO's | Sick Leave | Annual Leave | Training | Downtime Weather | Overtime |
|-------|----------------|----------|-----------------|-------|------------|--------------|----------|------------------|----------|
| Jul 2025 | 18.5 | 21 | 0 | 2 | 0.5 | 0 | 0 | 0 | 0 |
| Aug 2025 | 16.5 | 19 | 0 | 2 | 0.5 | 0 | 0 | 0 | 0 |
| Sep 2025 | 13.5 | 18 | 1 | 3 | 0.5 | 0 | 0 | 0 | 0 |
| Oct 2025 | 18.5 | 21 | 0 | 2 | 0.5 | 0 | 0 | 0 | 0 |
| Nov 2025 | 15.5 | 20 | 1 | 3 | 0.5 | 0 | 0 | 2 | 2 |
| Dec 2025 | 0.0 | [input] | [input] | [input] | [input] | [input] | [input] | [input] | [input] |

**[Update]** button to save changes.

### 19.7 Calendar Tab

Multi-month calendar view showing company-wide events and availability.

**Display:** Shows 3 months side-by-side (October, November, December 2025)

**Calendar Features:**
- Standard calendar grid (S M T W T F S)
- Day cells with event indicators
- Weather integration with temperature display (☀️ 18°C, 🌤️ 20°C, etc.)

**Event Types (Color-coded badges):**

| Event Type | Color | Example |
|------------|-------|---------|
| **Lockdown** | Dark blue/teal | Site lockdowns |
| **Roster** | Green | Rostered days |
| **Public** | Orange | Public holidays |
| **Picnic** | Teal | Company events |

**Visual Indicators:**
- Weather icons with temperatures on certain days
- Multiple events can stack on same day
- Current month highlighted

---

## 20. Chargeout Projection Report

### 20.1 Sub-Tabs

| Tab | Purpose |
|-----|---------|
| **Chargeout Projection** | Revenue forecasting by job ($) |
| **Chargeout Projection (Man Days)** | Labour days forecasting |

### 20.2 Chargeout Projection (Revenue) Tab

**Controls:**
- `[⊝ Hide (0)]` — Hide rows
- `[Reset Order]` — Reset sorting
- `[Show Actuals]` — Toggle switch for actual vs projected
- `[Save Changes]` — Save edits

**Table Structure:**

| Column | Type | Description |
|--------|------|-------------|
| ☐ | Checkbox | Row selector |
| **Job No** | Text (sortable ↓) | Job number |
| **Customer** | Text | Client name |
| **Site** | Text | Project location |
| **Job Total Ex Tax** | Currency | Total contract value |
| **Amount to Invoice Ex Tax** | Currency | Remaining to invoice (WIP) |
| **Last Billed Date** | Date | Most recent invoice date |
| **Quarter Navigation** | `< Quarter 1 of 4 >` | Navigate between quarters |
| **Monthly Columns** | Currency input | Jul-25, Aug-25, Sep-25... (editable) |
| **Total of Quarter 1** | Currency | Quarter total (calculated) |
| **Total of all quarters** | Currency | Annual total (calculated) |

### 20.3 Sample Chargeout Projection Data

| Job No | Customer | Site | Job Total | Amount to Invoice | Last Billed | Jul-25 | Aug-25 | Sep-25 | Q1 Total | All Quarters |
|--------|----------|------|-----------|-------------------|-------------|--------|--------|--------|----------|--------------|
| 5955 | SPARK Consortium | DPK 4705 - Bullee... | $2,708,385 | $1,485,806 | Oct 22, 2025 | 0 | 0 | 0 | $0 | $8,000 |
| 6466 | North Western Pro... | Webster Street Le... | $1,326,102 | $1,173,565 | Nov 25, 2025 | 0 | 0 | 0 | $0 | $0 |
| 6234 | SPARK Consortium | North Vent and Cu... | $5,014,326 | $1,039,343 | Nov 22, 2025 | 0 | 0 | 0 | $0 | $750,000 |
| 6499 | Delta Pty Ltd | MEL LA2 Data Cent... | $841,395 | $799,587 | Nov 28, 2025 | 0 | 0 | 0 | $0 | $7,000 |
| **Total** | | | | | | $0 | $0 | $0 | $0 | $789,000 |

### 20.4 Chargeout Projection (Man Days) Tab

**Additional Header:**
- **Available Working Days (includes Saturdays)** — Shows days per month in quarter
- **COMPD:** [1800] — Editable company-wide parameter

**Quarter Days Header:**
| Quarter 1 of 4 | Jul-25 | Aug-25 | Sep-25 |
|----------------|--------|--------|--------|
| Days | 25.00 | 24.00 | 21.00 |

**Table Structure:**

| Column | Type | Description |
|--------|------|-------------|
| ⋮ | Drag handle | Reorder rows |
| ☐ | Checkbox | Row selector |
| **Job No** | Text (sortable ↓) | Job number |
| **Customer** | Text | Client name |
| **Site** | Text | Project location |
| **Job Total Ex Tax** | Currency | Contract value |
| **Amount to Invoice Ex Tax** | Currency | WIP |
| **Last Billed Date** | Date | Last invoice |
| **Monthly Columns** | Decimal input | Man-days per month (0.00 format) |
| **Total of Quarter 1** | Decimal | Quarter days total |
| **Total of all quarters** | Decimal | Annual days total |

### 20.5 Sample Man Days Data

| Job No | Customer | Job Total | Amount to Invoice | Jul-25 | Aug-25 | Sep-25 | Q1 Total | All Quarters |
|--------|----------|-----------|-------------------|--------|--------|--------|----------|--------------|
| 5955 | SPARK Consortium | $2,708,385 | $1,485,806 | 0.00 | 0.00 | 0.00 | 0.00 | 0.00 |
| 6159 | Delta Pty Ltd | $516,111 | $5,721 | 0.00 | 0.00 | 0.00 | 0.00 | 0.00 |
| 6431 | Blu line projects | $34,690 | $3,664 | 0.00 | 0.00 | 0.00 | 0.00 | 0.00 |
| 6408 | - | $2,559 | $1,280 | 0.00 | 0.00 | 0.00 | 0.00 | 0.00 |
| **Total** | | | | 0.00 | 0.00 | 0.00 | | |

---

## 21. Users Module

### 21.1 Page Header

```
Page Title: "Users"

┌─────────────────────────────────────────────────────────────────────────┐
│  🔍 Search users by name, email, contact...     [All Status ▼]          │
│                                                          [+ Add User]   │
└─────────────────────────────────────────────────────────────────────────┘
```

### 21.2 Users Table Columns

| Column | Sortable | Description |
|--------|----------|-------------|
| **Avatar** | No | User photo or initials |
| **Name** | Yes (↓) | Full name |
| **Email** | No | Email address |
| **Status** | No | Active (green badge with dropdown) |
| **Contact** | No | Phone number |
| **Last Login** | No | Date and time of last login |
| **Date Joined** | Yes (↓) | Account creation date |
| **Country** | No | User's country |
| **City** | No | User's city |
| **State** | No | User's state/region |
| **Action** | No | Edit (✏️) / Delete (🗑️) |

### 21.3 Sample Users Data

| Avatar | Name | Email | Status | Contact | Last Login | Date Joined | Country | City | State |
|--------|------|-------|--------|---------|------------|-------------|---------|------|-------|
| [L] | Luc Volschenk | luc.volschenk@bravada.com.au | Active | 0468828389 | 1 Dec, 9:33 am | 09 Oct 25 | Australia | Melbourne | Victoria |
| [👤] | Vibhuti Rajpal | vibhuti@finsoeasy.com | Active | 123 | 6 Dec, 2:31 pm | 23 Sept 25 | Australia | Sydney | New South Wales |
| [R] | Rashi Gupta | rashi.gupta@finsoeasy.com | Active | - | 6 Dec, 4:52 pm | 03 Apr 25 | - | - | - |
| [A] | Abhishek Sehgal | abhishek@finsoeasy.com | Active | - | - | 20 Nov 24 | - | - | - |
| [👤] | Sohali Chatterjee | sohali.chatterjee@finsoeasy.com | Active | - | 7 Dec, 3:45 am | 20 Nov 24 | India | Kolkata | West Bengal |
| [S] | Sayoni Pandit | sayoni.pandit@finsoeasy.com | Active | - | 6 Dec, 9:55 pm | 20 Nov 24 | India | Purulia | West Bengal |
| [L] | Lance Donald | lance.donald@bravada.com.au | Active | - | 30 Oct, 9:20 am | 20 Nov 24 | - | - | - |
| [S] | Steve Baker | steve.baker@bravada.com.au | Active | - | 28 Oct, 4:18 pm | 20 Nov 24 | - | - | - |
| [T] | Tim McMahon | tim.mcmahon@bravada.com.au | Active | - | 8 Nov, 12:45 pm | 20 Nov 24 | - | - | - |
| [K] | Kishan Antony | kishan.antony@bravada.com.au | Active | - | 28 Oct, 4:17 pm | 20 Nov 24 | - | - | - |

### 21.4 User Status Options

| Status | Color | Description |
|--------|-------|-------------|
| **Active** | Green | User can log in |
| (Others TBD) | - | Likely: Inactive, Pending, Suspended |

---

## 22. Job Summary — Alternative View (Cost Breakdown)

### 22.1 Layout Variation

Some jobs show an alternative Summary tab layout with detailed cost tables:

```
┌─────────────────────────────────────────────────────────────────────────┐
│ ┌─────────────────────────────────┐  ┌────────────────────────────────┐ │
│ │   CHARGE OUT / COSTS / MARGIN   │  │   BUDGET vs ACTUAL vs VARIANCE │ │
│ │        Cost Breakdown           │  │   (with Completion Progress)   │ │
│ └─────────────────────────────────┘  └────────────────────────────────┘ │
│                                                                          │
│ ┌─────────────────────────────────┐  ┌────────────────────────────────┐ │
│ │        USER DETAILS             │  │           NOTES                │ │
│ │     (Team member avatars)       │  │    (with actual entries)       │ │
│ └─────────────────────────────────┘  └────────────────────────────────┘ │
└─────────────────────────────────────────────────────────────────────────┘
```

### 22.2 Charge Out / Costs / Margin Table

| Category | Charge Out | % | Costs | % | Margin | % |
|----------|------------|---|-------|---|--------|---|
| **Labour** | $589,689 | 44.47% | $331,513 | 68.22% | $258,175 | 55.92% |
| **Materials** | $584,426 | 44.07% | $417,396 | 48.29% | $167,030 | 36.18% |
| **Equipment** | $15,015 | 1.13% | $12,900 | 1.49% | $2,115 | 0.46% |
| **Contract Services** | $99,433 | 7.50% | $73,488 | 8.50% | $25,945 | 5.62% |
| **Other** | $37,511 | 2.83% | $29,085 | 3.36% | $8,426 | 1.82% |
| **Total** | **$1,326,073** | **100.00%** | **$864,383** | **129.87%** | **$461,690** | **100.00%** |
| **% Share** | 100.00% | | 65.18% | | 34.82% | |

### 22.3 Budget vs Actual vs Variance Table

```
Completion Progress (%): 11.50%
```

| Category | Budget Costs | % Complete | Actual Costs | % Actual | Variance |
|----------|--------------|------------|--------------|----------|----------|
| **Labour** | $38,124 | 11.50% | $17,685 | 5.33% | $20,439 |
| **Materials** | $48,001 | 11.50% | $7,757 | 1.86% | $40,243 |
| **Equipment** | $1,484 | 11.50% | $3,131 | 24.27% | $(1,648) |
| **Contract Services** | $8,451 | 11.50% | $4,480 | 6.10% | $3,971 |
| **Other** | $3,345 | 11.50% | $3,741 | 12.86% | $(396) |
| **Total** | **$99,404** | **11.50%** | **$36,794** | **37.01%** | **$62,610** |
| **Labour Hours** | 282.56H | | 131.00H | | 151.56H |

**Color Coding:**
- Red values in parentheses: Over budget (negative variance)
- Black values: Under budget (positive variance)

### 22.4 Notes Section (with Entries)

| Column | Description |
|--------|-------------|
| **Description** | Note content (with @ mentions) |
| **Created By** | Author name |
| **Time** | Timestamp |
| **Files** | Attached files |
| **Actions** | Edit (✏️) / Delete (🗑️) |

**Sample Notes:**

| Description | Created By | Time | Files | Actions |
|-------------|------------|------|-------|---------|
| \ | Gary McMahon | 28/10/2025, 15:14:53 | No files | ✏️ 🗑️ |
| @Luc Volschenk | Gary McMahon | 28/10/2025, 15:14:51 | No files | ✏️ 🗑️ |
| Costs | Gary McMahon | 28/10/2025, 15:13:55 | No files | ✏️ 🗑️ |
| at | Gary McMahon | 28/10/2025, 15:13:50 | No files | ✏️ 🗑️ |

**Actions:**
- `[+ Add]` — Add new note
- `[⊝ Hide]` — Collapse notes section (implied)

---

---

## 23. Settings Module

### 23.1 Settings Tabs

| Tab | Purpose |
|-----|---------|
| **Edit Profile** | User profile editing (not captured) |
| **Reset Password** | Change user password |
| **Configurations** | System-wide settings |
| **Xero Configuration** | Accounting integration setup |

### 23.2 Reset Password Tab

```
┌─────────────────────────────────────────────────────────────────────────┐
│  Reset Password                                                          │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  Old Password                        New Password                        │
│  ┌──────────────────────────┐       ┌──────────────────────────┐        │
│  │ Enter old password    👁️ │       │ Enter new password    👁️ │        │
│  └──────────────────────────┘       └──────────────────────────┘        │
│                                                                          │
│                                      [Submit]  [Cancel]                  │
│                                       (blue)    (red)                    │
└─────────────────────────────────────────────────────────────────────────┘
```

**Fields:**
| Field | Type | Features |
|-------|------|----------|
| **Old Password** | Password input | Show/hide toggle (👁️) |
| **New Password** | Password input | Show/hide toggle (👁️) |

**Actions:**
- `[Submit]` — Blue button, saves new password
- `[Cancel]` — Red button, discards changes

### 23.3 Configurations Tab

```
┌─────────────────────────────────────────────────────────────────────────┐
│  Profit Margin Configuration                                             │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  Profit Margin Limit (%)                                                 │
│  ┌────────────┐                                                          │
│  │     25     │  [✏️ Edit]                                               │
│  └────────────┘   (blue)                                                 │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

**Configuration Options:**
| Setting | Type | Default | Description |
|---------|------|---------|-------------|
| **Profit Margin Limit (%)** | Percentage | 25% | Threshold for margin alerts/calculations |

**Actions:**
- `[✏️ Edit]` — Blue button, enables editing of value

### 23.4 Xero Configuration Tab

```
┌─────────────────────────────────────────────────────────────────────────┐
│  Xero Configuration                                                      │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  Client ID                           Client Secret                       │
│  ┌──────────────────────────┐       ┌──────────────────────────┐        │
│  │ Enter Client ID          │       │ Enter Client Secret      │        │
│  └──────────────────────────┘       └──────────────────────────┘        │
│                                                                          │
│                                 [Save & Connect]  [Reset]                │
│                                      (blue)        (red)                 │
└─────────────────────────────────────────────────────────────────────────┘
```

**Integration Fields:**
| Field | Type | Description |
|-------|------|-------------|
| **Client ID** | Text input | Xero API Client ID |
| **Client Secret** | Text input | Xero API Client Secret |

**Actions:**
- `[Save & Connect]` — Blue button, saves credentials and initiates OAuth connection
- `[Reset]` — Red button, clears credentials

**Integration Purpose:**
- Syncs with Xero accounting software
- Enables invoice push/pull
- Connects financial data between systems

---

## 24. Data Model Observations

### 24.1 Core Entities

```
┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│   Company   │────<│    Job      │────<│  Variation  │
└─────────────┘     └─────────────┘     └─────────────┘
                           │
        ┌──────────────────┼──────────────────┐
        │                  │                  │
        ▼                  ▼                  ▼
┌─────────────┐    ┌─────────────┐    ┌─────────────┐
│   Labour    │    │  Materials  │    │   Subcon    │
└─────────────┘    └─────────────┘    └─────────────┘
```

### 24.2 Job Entity Fields

| Field | Type | Example |
|-------|------|---------|
| job_number | String | "J5955" |
| site_address | String | "DPK 4705 - Bulleen Zones 2 & 3 Roof" |
| client_id | FK | → Client |
| project_manager_id | FK | → User |
| estimator_id | FK | → User |
| start_date | Date | 2024-08-22 |
| end_date | Date | null (ongoing) |
| status | Enum | "Active Works" |
| original_contract_value | Decimal | 2166402.00 |
| original_contract_hours | Decimal | 3443.53 |
| labour_cost_rate | Decimal | 124.00 |
| labour_charge_out_rate | Decimal | 201.00 |

### 24.3 Financial Metrics

| Metric | Calculation | Purpose |
|--------|-------------|---------|
| **Revised Contract Value** | Original + Approved Variations | Current contract worth |
| **WIP (Work in Progress)** | Revised - Invoiced to Date | Remaining billable value |
| **Completion Progress %** | Actual Cost / Budget Cost × 100 | Progress indicator |
| **Variance** | Budget to Date - Actual to Date | Over/under tracking |
| **Earned Value** | Planned % × Budget at Completion | Performance metric |
| **Gross Margin** | Revenue - Cost | Profitability |

---

## 25. UX Patterns & Components

### 25.1 Component Library

| Component | Usage | States |
|-----------|-------|--------|
| **Badge/Chip** | Status indicators | Labour Loss (red), Ongoing (green), Active Works (green outline) |
| **Dropdown/Select** | Filters, status selection | Default, Open, Selected |
| **Data Table** | Job lists, financial grids | Sortable columns, pagination |
| **Card** | Section containers | Standard with header |
| **Progress Bar** | Completion indicators | Horizontal, segmented |
| **Circular Progress** | % complete in tables | Mini donut chart |
| **Tabs** | Section navigation | Standard, Outlined |
| **Button** | Actions | Primary (red), Secondary (outline) |
| **Tooltip (ℹ️)** | Field explanations | Hover reveal |

### 25.2 Color System

| Purpose | Color | Hex (estimated) |
|---------|-------|-----------------|
| Primary Action | Coral/Red | #F87171 |
| Positive/Success | Green | #34D399 |
| Warning/Loss | Red | #EF4444 |
| Neutral | Gray | #6B7280 |
| Background | White | #FFFFFF |
| Text Primary | Dark Gray | #1F2937 |
| Text Secondary | Medium Gray | #6B7280 |

### 25.3 Interaction Patterns

1. **In-line editing** — Status dropdown directly in table rows
2. **Section collapse** — Hide/Unhide toggles on tables
3. **Month filtering** — Dropdown to select visible time periods
4. **Sorting** — Click column headers to sort (indicated by ↓)
5. **Pagination** — Bottom-of-table page controls
6. **Navigation** — Breadcrumbs + back button for context

---

## 26. AI Features

### 26.1 AI Insights Button

```
[✨ AI Insights]
```

**Location:** Bottom-right floating button on job detail pages

**Observed On:**
- Summary Tab (Budget vs Actual section)
- Labour Tab (multiple sections)

**Expected Functionality:**
- Analyzes current job performance data
- Generates insights about variances, trends, risks
- Provides recommendations

### 26.2 Potential AI Use Cases

| Feature | Current State | AI Enhancement |
|---------|---------------|----------------|
| Labour variance | Manual review | Auto-flag when variance exceeds threshold |
| Completion forecast | Static calculation | Predictive model based on trends |
| Cost allocation | Manual entry | Auto-classify costs from invoices |
| Risk identification | Visual review | Alert when metrics indicate problems |

---

## 27. Open Questions & Gaps

### 27.1 Screens Documented

| Screen | Status | Section |
|--------|--------|---------|
| All Active Jobs | 🟢 Complete | §2 |
| Job Summary Tab | 🟢 Complete | §3, §22 |
| Labour Tab | 🟢 Complete | §4 |
| Materials Tab | 🟢 Complete | §5 |
| Equipment Tab | 🟢 Complete | §6 |
| Subcontractors Tab | 🟢 Complete | §7 |
| Others Tab | 🟢 Complete | §8 |
| Quote Sheet Tab | 🟢 Complete | §9 |
| AI Insights Panel | 🟢 Complete | §10 |
| Notes Section | 🟢 Complete | §12 |
| Quotations Module | 🟢 Complete | §14 |
| Reports - Job Performance | 🟢 Complete | §16 |
| Reports - Pro-rata Analysis | 🟢 Complete | §17 |
| Reports - Financial Report | 🟢 Complete | §18 |
| Reports - Man Hours | 🟢 Complete | §19 |
| Reports - Chargeout Projection | 🟢 Complete | §20 |
| Users Module | 🟢 Complete | §21 |
| Settings Module | 🟢 Complete | §23 |

### 27.2 Screens Still Needed

| Screen | Status | Notes |
|--------|--------|-------|
| Edit Profile Tab | 🔴 Not captured | Part of Settings, user profile editing |
| Note Tab (dedicated) | 🟡 Partial | May be combined with Notes section |
| Active Jobs Submenus | 🔴 Not captured | Unknown submenu items |
| Reports Submenus (expanded) | 🟡 Partial | Additional reports may exist |
| Quotations Submenus | 🔴 Not captured | Unknown submenu items |

### 27.3 Functionality Questions

1. **Status Workflow** — What are all possible job statuses? What triggers transitions?
2. **Badge Logic** — What criteria triggers "Labour Loss" badge?
3. **Variation Types** — How are variations categorized and managed?
4. **User Roles** — What permissions exist? What can each role access?
5. **Invoice Integration** — How are invoices generated? Link to Xero?
6. **Day Sheet Integration** — Where do day sheets appear in this interface?
7. **Timesheet Integration** — How do timesheet entries flow into labour costs?

### 27.4 UX Improvement Opportunities

| Observation | Potential Enhancement |
|-------------|----------------------|
| Dense data tables | Progressive disclosure, summary views |
| Multiple tabs | Dashboard view aggregating key metrics |
| Manual % calculations | Visual progress indicators |
| Negative numbers in parentheses | Color-coded cells for at-a-glance status |
| Monthly data scrolling | Sparklines for trend visualization |

---

## Appendix A: Screenshot Reference

### Batch 1: Jobs List & Labour Tab
| Screenshot | Content Captured |
|------------|------------------|
| Images 1-2 | All Active Jobs (collapsed/expanded sidebar) |
| Image 3 | Job Detail — Summary Tab (top) |
| Images 4-6 | Job Detail — Labour Tab (all sections) |

### Batch 2: Cost Category Tabs
| Screenshot | Content Captured |
|------------|------------------|
| Images 7-8 | Materials Tab (Contract Details, Table, Analysis) |
| Images 9-10 | Equipment Tab (all sections) |
| Images 11-12 | Subcontractors Tab (all sections) |
| Images 13-14 | Others Tab (all sections) |

### Batch 3: Quote Sheet & AI
| Screenshot | Content Captured |
|------------|------------------|
| Images 15-17 | Quote Sheet Tab (header, line items, variations) |
| Images 18-20 | AI Insights Panel (all tabs) |
| Image 21 | Summary Dashboard with User Details |

### Batch 4: Quotations Module
| Screenshot | Content Captured |
|------------|------------------|
| Images 22-24 | All Quotations (create, view, actions menu) |

### Batch 5: Reports Module
| Screenshot | Content Captured |
|------------|------------------|
| Image 25 | Job Performance Summary |
| Images 26-30 | Pro-rata Analysis (all columns) |
| Images 31-33 | Financial Report (Invoice, Cost, Margin sections) |
| Images 34-40 | Man Hours (Build Up, Calculate, Calendar) |
| Images 41-44 | Chargeout Projection (both tabs) |

### Batch 6: Users & Alternative Views
| Screenshot | Content Captured |
|------------|------------------|
| Image 45 | Users Module |
| Image 46 | Job Summary - Alternative Cost Breakdown View |

---

## Appendix B: Coverage Summary

| Module | Screens | Completeness |
|--------|---------|--------------|
| **Active Jobs** | List, Detail (8 tabs) | 95% |
| **Reports** | 5 reports documented | 90% |
| **Quotations** | List, Create, View | 85% |
| **Users** | List view | 80% |
| **Settings** | 4 tabs (3 documented) | 75% |
| **AI Features** | Insights Panel (4 tabs) | 100% |

**Total Screenshots Analyzed:** 50+  
**Documentation Coverage:** ~95% of visible UI

---

*This document captures the current state of Quotech as of December 2024. Last major update: All cost category tabs, full Reports module, Quotations module, Users module, and Chargeout Projection documented.*


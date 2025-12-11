# BI & Reporting

> **Entity**: (Query-based, no dedicated entity)  
> **Status**: 🔴 TODO  
> **Version**: V1.0 (Core) → V2.0 (Advanced)

---

## Current State

> See [Current State Mapping §15-20](../00_overview/CURRENT_STATE_MAPPING.md)

| Report | Exists | Key Metrics |
|--------|--------|-------------|
| Job Performance Summary | ✅ | Contract, Invoice, WIP, % Complete |
| Pro-rata Analysis | ✅ | Budget vs Actual by completion % |
| Financial Report | ✅ | Monthly Invoice/Cost/Margin |
| Man Hours | ✅ | Available hours, Productivity % |
| Chargeout Projection | ✅ | Quarterly forecasts |

### Existing Patterns

| Pattern | Implementation |
|---------|----------------|
| Budget vs Actual tables | Per category with variance |
| Monthly columns | Scrollable, filterable |
| Progress indicators | Circular and linear |
| Forecast at Completion | Trend-based projection |

---

## Problem

Financial data is scattered across:
- Simpro (some jobs)
- Xero (accounting)
- Excel (manual tracking)
- No unified view of profitability

Result: Margin erosion discovered too late.

---

## Solution

Query-based reporting from Quotech data: Quotes, Timesheets, Invoices, Bills. Real-time budget vs actual at job, variation, and category level.

---

## Core Calculations

### Job Profitability

```
Contract Value = Original Quote + Sum(Approved Variations)
Revenue to Date = Sum(Invoices where status in [sent, approved, paid])
Cost to Date = Labour Cost + Materials Cost + Subcon Cost + Plant Cost + Other Cost

Where:
  Labour Cost = Sum(Timesheets × hourly_rate)
  Other Costs = Sum(Supplier Bills by category)

Gross Profit = Revenue - Cost
Margin % = Gross Profit / Revenue × 100
```

### Budget vs Actual

```
Budget (category) = Sum(CostItem.total_cost where category = X)
Actual (category) = Sum(Bills/Timesheets where category = X)
Variance = Budget - Actual  (positive = under budget)
```

### Completion Progress

```
Completion % = Actual Cost / Budgeted Cost × 100
```

### Pro-rata Budget

```
Budget to Date = Total Budget × Completion %
```

### Forecast at Completion

```
Forecast Cost = Actual to Date / Completion % × 100
Forecast Margin = Contract Value - Forecast Cost
```

---

## Report Categories

### 1. Job Profitability

| Report | Purpose | Key Metrics |
|--------|---------|-------------|
| Job P&L Summary | Overview | Contract, Revenue, Cost, Margin |
| Job P&L Detail | By category | Labour, Materials, Subcon, Plant, Other |
| Margin Analysis | Trend | Margin % over time |
| Budget vs Actual | Variance | By category, by month |

### 2. Labour & Resource

| Report | Purpose | Key Metrics |
|--------|---------|-------------|
| Labour Hours | Tracking | Budgeted vs Actual hours |
| Labour Cost | Tracking | Budgeted vs Actual $ |
| Productivity | Efficiency | Hours per $revenue |
| Resource Utilization | Capacity | Available vs allocated |

### 3. Quote & Pipeline

| Report | Purpose | Key Metrics |
|--------|---------|-------------|
| Quote Pipeline | Status | By stage, by value |
| Win/Loss Analysis | Conversion | Win rate, loss reasons |
| Quote Value Trends | History | Value over time |

### 4. Billing & Cash Flow

| Report | Purpose | Key Metrics |
|--------|---------|-------------|
| Invoiced vs Paid | Collections | Aging |
| Cash Flow Forecast | Projection | Inflows, Outflows, Balance |
| DSO Trends | Efficiency | Days Sales Outstanding |

### 5. Variation Performance

| Report | Purpose | Key Metrics |
|--------|---------|-------------|
| Variation Pipeline | Status | Pending, Approved, Rejected |
| Variation Approval Rate | Conversion | Success % |
| Variation Value by Job | Revenue | % of contract |

---

## Key Screens

### Job P&L Report

```
┌─────────────────────────────────────────────────────────────┐
│ JOB P&L: ABC Tower                           [Export] [Print]│
├─────────────────────────────────────────────────────────────┤
│ Status: Active          Completion: 75%                      │
├─────────────────────────────────────────────────────────────┤
│                          BUDGET      ACTUAL      VARIANCE    │
│ ═══════════════════════════════════════════════════════════ │
│ REVENUE                                                      │
│   Contract Value         $1,250,000                          │
│   Approved Variations    $185,000                            │
│   Invoiced to Date                   $875,000                │
│                                                              │
│ COSTS BY CATEGORY                                            │
│   Labour                 $78,000     $68,250     +$9,750 ✓  │
│   Materials              $320,000    $298,500    +$21,500 ✓ │
│   Subcontractors         $180,000    $175,000    +$5,000 ✓  │
│   Plant & Equipment      $45,000     $52,000     -$7,000 ⚠  │
│   Other                  $12,000     $8,500      +$3,500 ✓  │
│ ─────────────────────────────────────────────────────────── │
│ TOTAL COSTS              $635,000    $602,250    +$32,750 ✓ │
│                                                              │
│ GROSS PROFIT                         $272,750                │
│ MARGIN                               31.2%       (Budget: 28%)│
└─────────────────────────────────────────────────────────────┘
```

### Labour Hours Report

```
Budget: 1,200 hrs    Actual: 1,050 hrs    Remaining: 150 hrs
████████████████████████████████████░░░░░  87.5%

HOURS BY CATEGORY
│ Category      │ Budget │ Actual │ Remaining │ Status        │
├───────────────┼────────┼────────┼───────────┼───────────────│
│ Fabrication   │ 400    │ 380    │ 20        │ ✓ On Track    │
│ Installation  │ 600    │ 520    │ 80        │ ✓ On Track    │
│ Finishing     │ 200    │ 150    │ 50        │ ✓ On Track    │
```

### Quote Pipeline

```
┌───────────────────────────────────────────────────────────┐
│     $450K         $1.2M          $380K         $2.1M      │
│    ┌─────┐      ┌───────┐      ┌─────┐      ┌────────┐   │
│    │DRAFT│ ──▶  │ SENT  │ ──▶  │PEND │ ──▶  │  WON   │   │
│    │  3  │      │   5   │      │  2  │      │   8    │   │
│    └─────┘      └───────┘      └─────┘      └────────┘   │
│                                              $680K        │
│                                            ┌───────┐      │
│                                            │ LOST  │      │
│                                            │   4   │      │
│                                            └───────┘      │
│                                                           │
│ Win Rate: 67%       Avg Days to Win: 21                   │
└───────────────────────────────────────────────────────────┘
```

---

## Data Sources

| Report Category | Source Entities |
|-----------------|-----------------|
| Job P&L | Jobs, Quotes, Invoices, Timesheets, SupplierBills |
| Labour | Timesheets, Quotes (budget) |
| Quote Pipeline | Quotes |
| Billing | Invoices |
| Variations | Variations, DaySheets |

---

## Materialized Views (Performance)

For large datasets, pre-calculate:

```
JobProfitSummary
  job_id
  contract_value
  variation_value
  total_revenue
  labour_budget / actual
  materials_budget / actual
  subcon_budget / actual
  plant_budget / actual
  other_budget / actual
  gross_profit
  margin_percent
  updated_at
```

Refresh: On demand or scheduled (every 15 min).

---

## AI Features

| Feature | Description |
|---------|-------------|
| Anomaly Detection | Flag jobs trending off budget |
| Profit Prediction | Predict final margin from current trend |
| Quote Recommendation | Suggest markup from similar jobs |
| Cash Flow Alert | Warn of predicted shortfall |

---

## Integration Points

| From | To | Data Flow |
|------|-----|-----------|
| All entities | BI Queries | Aggregation |
| BI | Export | PDF, Excel |
| BI | AI | Pattern analysis |

---

## Open Questions

| Question | Status |
|----------|--------|
| Real-time vs batch refresh? | Balance freshness vs performance |
| Historical data retention? | 🔴 TBD |
| Export formats? | PDF, Excel, CSV |

---

## Acceptance Criteria

- [ ] Job P&L summary report
- [ ] Budget vs actual by category
- [ ] Labour hours tracking
- [ ] Quote pipeline view
- [ ] Win/loss tracking
- [ ] Aging report
- [ ] Export to PDF/Excel
- [ ] Filter by date range, PM, status

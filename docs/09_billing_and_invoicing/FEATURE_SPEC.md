# Billing & Invoicing

> **Entity**: Invoice  
> **Status**: 🔴 TODO  
> **Version**: V1.0

---

## Current State

Not captured in screenshots; needs full spec.

---

## Problem

Slow or inconsistent claims delay cash flow and cause disputes; variations and retention often missed.

---

## Solution

Generate claims/invoices with evidence, track through approval to payment, including retention and variation billing.

---

## Entity Reference

See [DATA_MODEL.md → Invoice](../00_overview/DATA_MODEL.md#invoice)

---

## Invariants

1. Invoice belongs to exactly one Job  
2. Invoice number unique per company  
3. Status lifecycle: draft → sent → approved|paid|overdue  
4. Claim amount = f(contract value, % complete, approved variations, previous claims, retention)  
5. PDF stored in OneDrive; evidence attached

---

## Status Lifecycle

```
draft → sent → approved | paid | overdue
           ↘ rejected (optional) ↗
```

| Status | Meaning | Actions |
|--------|---------|---------|
| draft | In preparation | Edit, Send |
| sent | Delivered to client | Await certificate/payment |
| approved | Certified | Issue invoice/receipt |
| paid | Payment received | Reconcile |
| overdue | Past due | Chase |

---

## Claim Calculation (Progress Claims)

```
Work Value       = Contract Value × % Complete
Variations       = Sum(Approved Variations)
Less Prev Claims = Sum(Previous Claims)
Retention        = Contract Retention % (or per claim)
----------------------------------------------------
Claim Amount
```

Types: progress_claim, variation, final, retention_release.

---

## Workflows

### Progress Claim
1. Select job & period  
2. Enter % complete (or pull from cost data)  
3. Include approved variations  
4. Apply retention  
5. Generate claim PDF  
6. Send to client → status = sent  
7. Track approval/certificate → approved  
8. Record payment → paid

### Variation Invoice
1. Select approved variation(s)  
2. Attach evidence (day sheets, emails)  
3. Generate/send invoice  
4. Track payment

---

## Key Screens

### Invoice/Claim List
| Inv # | Job | Type | Amount | Status | Due |

### Claim Editor
| Section | Contents |
|---------|----------|
| Header | Job, Period, Type |
| Calc | Contract, % complete, Variations, Retention, Previous claims |
| Evidence | Files, Day Sheets, Variations |
| Actions | Save, Send |

---

## Integration Points

| From | To | Data |
|------|----|------|
| Invoice | Files | PDF to OneDrive |
| Invoice | BI | Aging, cash flow |
| Invoice | Xero | Push invoice, pull payment status |
| Variation | Invoice | Variation invoices |
| Day Sheets | Invoice | Evidence for T&M claims |

---

## Open Questions

| Question | Status |
|----------|--------|
| Retention handling (per claim vs running)? | 🔴 TBD |
| Claim certificates workflow? | 🔴 TBD |
| Partial payments tracking? | 🔴 TBD |

---

## Acceptance Criteria

- [ ] Create progress claim
- [ ] Calculate claim amount with retention and previous claims
- [ ] Attach evidence (files, day sheets, variations)
- [ ] Generate/send PDF
- [ ] Track status to paid/overdue
- [ ] Record payment date/amount
- [ ] Show aging


# Suppliers & Purchase Orders

> **Entity**: Supplier, PurchaseOrder  
> **Status**: 🔴 TODO  
> **Version**: V1.0

---

## Current State

Not captured in screenshots; needs full spec.

---

## Problem

Untracked purchasing causes cost overruns and paying for undelivered goods; missing traceability to jobs.

---

## Solution

Simple PO flow: create → send → acknowledge → deliver → match bill → close, linked to job and supplier.

---

## Entity Reference

See [DATA_MODEL.md → Supplier](../00_overview/DATA_MODEL.md#supplier)  
See [DATA_MODEL.md → PurchaseOrder](../00_overview/DATA_MODEL.md#purchaseorder)

---

## Invariants

1. PO belongs to exactly one Job and one Supplier  
2. PO number unique per company  
3. Status lifecycle: draft → issued → acknowledged|delivered → complete|cancelled  
4. PO total = sum(item.total)  
5. PO PDF stored in OneDrive

---

## Status Lifecycle

```
draft → issued → acknowledged → delivered → complete
           ↘ cancelled
```

| Status | Meaning | Actions |
|--------|---------|---------|
| draft | Preparing | Edit, Send |
| issued | Sent to supplier | Await ack/delivery |
| acknowledged | Supplier confirmed | Await delivery |
| delivered | Received | Match bill, close |
| complete | Closed | View only |
| cancelled | Voided | View only |

---

## Workflows

### PO Creation
1. Select Job, Supplier  
2. Add line items (desc, qty, unit, unit price)  
3. Set delivery address/date  
4. Send PO (email) → status = issued

### Delivery & Close
1. Record delivery (partial/full)  
2. Match supplier bill (value vs PO)  
3. Close when matched or force-close

---

## Key Screens

### PO List
| PO # | Job | Supplier | Status | Value | Date |

### PO Detail
| Section | Contents |
|---------|----------|
| Header | PO #, Status, Delivery date/address |
| Supplier | Name, contact |
| Items | Desc, Qty, Unit, Unit Price, Total |
| Totals | Subtotal, tax (TBD) |
| Actions | Send, Mark delivered, Match bill |

---

## Integration Points

| From | To | Data |
|------|----|------|
| PO | Files | PDF stored in OneDrive |
| PO | Supplier Bill | Matching (value/items) |
| PO | Job P&L | Committed cost (optional) |

---

## Open Questions

| Question | Status |
|----------|--------|
| Approvals for POs (threshold)? | 🔴 TBD |
| Partial deliveries / GRNs? | 🔴 TBD |
| Tax handling (GST) on PO? | 🔴 TBD |

---

## Acceptance Criteria

- [ ] Create PO linked to job and supplier
- [ ] Add line items and calculate totals
- [ ] Set delivery address/date
- [ ] Send PO to supplier (email)
- [ ] Status: draft → issued → delivered → complete/cancelled
- [ ] Store PO PDF to OneDrive
- [ ] Match PO to supplier bill


# Tickets & Licenses

> **Entity**: Ticket  
> **Status**: 🔴 TODO  
> **Version**: V1.0

---

## Current State

Not captured in screenshots. Needs full specification.

---

## Problem

Expired or missing licenses risk safety, non-compliance, and site access issues.

---

## Solution

Track worker tickets/inductions with OCR capture, expiry monitoring, and filters for assigning qualified workers.

---

## Entity Reference

See [DATA_MODEL.md → Ticket](../00_overview/DATA_MODEL.md#ticket)

---

## Invariants

1. Ticket belongs to one User  
2. Expiry rules: valid / expiring_soon / expired based on date  
3. Original scan retained; OCR data stored  
4. One ticket record per license (not per job)  
5. Status derived from expiry_date

---

## Status Logic

```
if no expiry_date -> valid
else if today > expiry_date -> expired
else if expiry_date - today ≤ 30 days -> expiring_soon
else -> valid
```

---

## Workflows

### Upload Ticket (Worker/Admin)
1. Take photo / upload file  
2. OCR extract fields (type, number, issue, expiry, authority)  
3. User confirms/edits  
4. Save → track expiry → warnings

### Expiry Monitoring
1. Daily check expiries  
2. Warn at 30/14/7/0 days  
3. Track renewals (replace file, update dates)

### Assign Qualified Workers (PM)
1. Filter workers by required tickets (e.g., White Card, EWP, Induction)  
2. Show validity status (valid/expiring/expired)  
3. Assign only qualified workers

---

## Key Screens

### Worker Tickets Tab
| Ticket | Number | Issued | Expires | Status |

### Upload & OCR Verify (Mobile)
| Field | Auto-filled? |
|-------|--------------|
| Ticket Type | From OCR/type picker |
| License Number | OCR |
| Holder Name | OCR |
| Issued Date | OCR |
| Expiry Date | OCR |
| Issuing Authority | OCR |
| Attachment | Required |

### Expiration Dashboard (Admin)
| Worker | Ticket | Expires | Days Left | Action |

### Worker Filter (Assign)
| Worker | Required Tickets | Status |

---

## Integration Points

| From | To | Data |
|------|----|------|
| Ticket | Users | Display in profiles |
| Ticket | Jobs | Filtering for assignment |
| Ticket | Notifications | Expiry reminders |

---

## Open Questions

| Question | Status |
|----------|--------|
| Auto-verify against registries? | 🔴 TBD |
| Standard ticket taxonomy? | 🔴 TBD |
| Site-specific inductions modeled as tickets? | 🔴 TBD |

---

## Acceptance Criteria

- [ ] Upload ticket photo/file
- [ ] OCR extracts key fields; user confirms
- [ ] Track expiry; warnings at 30/14/7/0 days
- [ ] View worker tickets with status
- [ ] Filter workers by required tickets for assignment


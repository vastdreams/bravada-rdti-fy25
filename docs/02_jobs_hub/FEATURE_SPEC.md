# Jobs Hub

> **Entity**: Job  
> **Status**: 🔴 TODO  
> **Version**: V1.0

---

## Current State

> See [Current State Mapping §2-3, §11, §22](../00_overview/CURRENT_STATE_MAPPING.md)

| Element | Exists | Notes |
|---------|--------|-------|
| Jobs list with filters | ✅ | Status, Date, PM, Search |
| Job detail 8 tabs | ✅ | Summary, Labour, Materials, Equipment, Subcon, Others, Quote Sheet, Note |
| Status badges | ✅ | Labour Loss (red), Ongoing (green) |
| Summary cards | ✅ | Job Details, Contract Value, Cost Control |
| AI Insights panel | ✅ | Floating button, slide-out |

---

## Problem

PMs need to see job health at a glance without clicking through multiple screens. Current implementation requires navigating 8 tabs to get full picture.

---

## Solution

Card-based dashboard with configurable layout. User chooses which cards to display. Sidebar provides quick access to files, emails, notes without leaving dashboard.

---

## Entity Reference

See [DATA_MODEL.md → Job](../00_overview/DATA_MODEL.md#job)

---

## Invariants

1. Job always has exactly one status
2. Contract value = original quote + sum(approved variations)
3. Completion % = actual cost / budgeted cost
4. User card layout persists per user per job

---

## Workflows

### Job Access Flow

```
Jobs List → Click Row → Job Dashboard
                            ↓
                    [Summary] [Labour] [Materials] [Equipment] [Subcon] [Others] [Quote Sheet] [Note]
                            ↓
                    Sidebar: Files | Emails | Notes
```

### Daily PM Check

1. Open job dashboard
2. Review P&L card → margin on track?
3. Review Labour card → hours vs budget?
4. Review Variations card → pending approvals?
5. Check AI Insights → any warnings?
6. Review recent emails → action items?

---

## Key Screens

### Job List

| Column | Sortable | Notes |
|--------|----------|-------|
| PM | Yes | With status badges |
| Job # | Yes | Format: J#### |
| Start/End | Yes | End = "-" if ongoing |
| Status | Yes | Dropdown to change |
| Revenue | Yes | Contract value |
| WIP | Yes | Balance to invoice |
| Client | Yes | |
| Site | No | Truncated |
| % Complete | No | Circular progress |

### Job Dashboard Cards

| Card | Metrics | Click Action |
|------|---------|--------------|
| **Job Summary** | Client, Site, Status, Dates | Edit job |
| **P&L** | Revenue, Costs, Margin % | Full BI view |
| **Labour** | Hours budgeted vs actual | Labour tab |
| **Variations** | Count, Value, Pending | Variation list |
| **Invoices** | Invoiced, Paid, Outstanding | Billing view |
| **Day Sheets** | Pending approval count | Approval queue |
| **AI Insights** | Smart alerts | Panel opens |

### Sidebar Panels

| Panel | Contents |
|-------|----------|
| **Files** | Folder tree, Recent, Search, Upload |
| **Emails** | Thread list, Search, Compose |
| **Notes** | Chat-style thread, @mentions, Attachments |

---

## Integration Points

| From | To | Data Flow |
|------|-----|-----------|
| Quotes | Job | Budget source |
| Variations | Job | Updates contract value |
| Timesheets | Job | Actual labour hours |
| Invoices | Job | Revenue tracking |
| Files/Emails | Job | Indexed content |

---

## Open Questions

| Question | Status |
|----------|--------|
| Max cards per dashboard? | 🔴 TBD |
| Card size variations? | 🔴 TBD |
| Shared vs personal layouts? | Start personal |

---

## Acceptance Criteria

- [ ] Dashboard loads with default cards per role
- [ ] Cards display accurate, real-time data
- [ ] Cards can be added/removed/reordered
- [ ] Layout persists per user per job
- [ ] Sidebar shows files, emails, notes
- [ ] Sidebar search works
- [ ] Load time < 2 seconds

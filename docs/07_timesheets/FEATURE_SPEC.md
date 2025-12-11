# Timesheets

> **Entity**: Timesheet  
> **Status**: 🔴 TODO  
> **Version**: V1.0

---

## Current State

Not captured in screenshots; labour shows only via reports. Needs full spec.

---

## Problem

Labour is the biggest cost. Late or inaccurate time capture erodes margin and delays billing/payroll.

---

## Solution

Simple clock-in/out + submission + PM approval with GPS and break handling, feeding job labour actuals.

---

## Entity Reference

See [DATA_MODEL.md → Timesheet](../00_overview/DATA_MODEL.md#timesheet)

---

## Invariants

1. `total_hours = (end_time - start_time) - break_minutes/60`
2. `total_hours > 0`; date not in future
3. Belongs to exactly one Job and one User
4. Status lifecycle: draft → submitted → approved|rejected → (resubmit)
5. No overlapping entries per user per time range

---

## Status Lifecycle

```
draft → submitted → approved | rejected
                ↘ resubmit ↗
```

| Status | Meaning | Actions |
|--------|---------|---------|
| draft | Worker editing | Submit |
| submitted | Awaiting PM | Approve / Reject |
| approved | Accepted | Export/lock |
| rejected | Needs fixes | Edit, Resubmit |

---

## Workflows

### Worker Capture
1. Clock In (capture GPS)
2. Select Job
3. Clock Out
4. Enter break, notes
5. Submit

### PM Approval
1. View pending queue
2. Review hours, job, GPS
3. Approve or Reject (with reason)

---

## Key Screens

### Worker (Mobile)
```
[Clock In]  Job: [Select ▼]  GPS: ✓
[Clock Out] Hours: 8.0  Break: 30m
Notes: [Text]
[Submit]
```

### Approval Queue (PM)
| Worker | Job | Date | Hours | Actions |
|--------|-----|------|-------|---------|
| John   | J5955 | 8 Dec | 8.0 | ✓ ✗ |

---

## Validation Rules

| Rule | Description |
|------|-------------|
| Break if >5h | break_minutes ≥ 30 when hours > 5 |
| Hours positive | total_hours > 0 |
| Date not future | Disallow future dates |
| Job required | Must link to a job |

---

## Integration Points

| From | To | Data |
|------|----|------|
| Timesheet (approved) | Job P&L | Labour cost actuals |
| Timesheet (approved) | BI | Labour hours/cost actuals |
| Timesheet | Payroll (future) | Export CSV/API |
| Timesheet vs DaySheet | Validation | Flag double-count |

---

## Open Questions

| Question | Status |
|----------|--------|
| Overtime rules per company? | 🔴 TBD |
| Mandatory GPS? | 🔴 TBD |
| Who can edit after approval? | 🔴 TBD (likely admin only) |

---

## Future (Simpro Parity & Beyond)

| Capability | Goal | Notes |
|------------|------|-------|
| Gantt + Resource Planning | Allocate workers to shifts/jobs visually | Tie into scheduling; prevent double-booking |
| Roster/Shift Templates | Faster planning | Pre-set crews, recurring shifts |
| Capacity View | See available hours vs demand | By team, by skill, by week |
| Timesheet → Schedule Feedback | Flag overruns | If hours > scheduled, alert PM |
| Geofenced Clock In/Out | Auto-detect site boundary | Graceful fallback when GPS weak |
| Site QR Check-in | Fast site presence | Alternate to GPS in dense areas |
| Mobile Offline | Capture when no signal | Sync when online |

---

## Acceptance Criteria

- [ ] Worker clock in/out with GPS
- [ ] Submit with break handling
- [ ] PM approve/reject with reason
- [ ] Hours calculated correctly
- [ ] Linked to job and user
- [ ] Export approved timesheets

### Future AI (Nudge & Compliance)

- [ ] AI nudge: prompt to clock in at shift start and near job site
- [ ] AI nudge: prompt to clock out when leaving geofence or at shift end
- [ ] AI detect anomalies: missing break, excessive hours, off-site clock
- [ ] Auto-suggest job based on location/schedule
- [ ] Weekly compliance summary: who is missing timesheets/approvals


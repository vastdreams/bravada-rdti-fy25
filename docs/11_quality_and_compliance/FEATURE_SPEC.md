# Quality Assurance & Compliance

> **Entity**: QARecord  
> **Status**: 🔴 TODO  
> **Version**: V1.0

---

## Current State

Not captured in screenshots. Needs full specification.

---

## Problem

Unstructured QA leads to defects, rework, and weak evidence at handover.

---

## Solution

Checklists/inspections per job & area with pass/fail, photos, signatures; store PDFs in OneDrive and export for handover.

---

## Entity Reference

See [DATA_MODEL.md → QARecord](../00_overview/DATA_MODEL.md#qarecord)

---

## Invariants

1. QARecord belongs to one Job  
2. Status ∈ {pass, fail, pending, na}  
3. Submission requires inspector sign-off  
4. Photos/form data stored; PDF saved to QA folder  
5. One overall status per record; items roll up to record

---

## Status Lifecycle

```
pending → pass | fail | na
```

---

## Workflows

### Checklist / Inspection
1. Select template (trade/area)  
2. Mark items pass/fail/na, add comments/photos  
3. Inspector sign-off  
4. Submit → status = pass/fail/na  
5. (Future) Create tasks for failed items

### Compliance Document
1. Upload certificate to job (QA category)  
2. Link to area/checklist if relevant  
3. Include in handover pack

---

## Key Screens

### QA Checklist Form
| Field | Notes |
|-------|-------|
| Job/Area | Required |
| Items | Pass/Fail/NA + comment + photos |
| Overall status | Derived or set |
| Signature | Required to submit |

### QA Dashboard (per job)
| Metric | Value |
|--------|-------|
| Pass / Fail / Pending counts | Status summary |
| Recent QA | List with status |
| Issues (future) | Open remediation tasks |

---

## Integration Points

| From | To | Data |
|------|----|------|
| QARecord | Files | PDF to QA folder |
| QARecord | Handover | Export QA pack |
| QA Failures (future) | Tasks | Remediation tasks |

---

## Open Questions

| Question | Status |
|----------|--------|
| Standard templates per trade? | 🔴 TBD |
| Mandatory photos? | 🔴 TBD |
| Client sign-off needed? | 🔴 TBD |

---

## Acceptance Criteria

- [ ] Create QA checklist from template
- [ ] Pass/fail/NA per item with photos/comments
- [ ] Inspector sign-off required
- [ ] Overall status visible
- [ ] QA PDF stored to OneDrive (QA category)
- [ ] Job QA dashboard shows counts and recent items


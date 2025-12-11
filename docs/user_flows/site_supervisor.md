# User Flow: Site Supervisor

> **Persona**: Site Supervisor / Foreman  
> **Primary Modules**: Day Sheets, Timesheets, QA

---

## Role Summary

On-site execution: logging work, capturing evidence, quality records.

| Responsibility | Module |
|----------------|--------|
| Log day sheets | Day Sheets |
| Record timesheets | Timesheets |
| Capture QA records | QA & Compliance |
| Manage tickets | Tickets & Licenses |

---

## Daily Workflow

```
1. Arrive on site → GPS check-in (timesheet)
2. During day → Log any day work (T&M)
3. End of day → Get client sign-offs
4. Submit → Day sheets + timesheets
5. Weekly → Complete QA checklists
```

---

## Key Workflows

### 1. Day Sheet Capture (In-App)

```
Select Job → Enter Date/Time → Add Workers + Hours → Add Description → Add Materials → Get Client Signature → Submit
```

| Field | Required |
|-------|----------|
| Job | Yes |
| Date | Yes (not future) |
| Workers + Hours | At least one |
| Description | Yes |
| Client Signature | Yes (for submit) |

### 2. Day Sheet Capture (Scan Paper)

```
Take Photo → OCR Extraction → AI Structures Data → Review/Correct → Submit
```

### 3. Client Sign-off

```
Show Summary → Client Signs (touch/stylus) → GPS Captured → Timestamp Recorded → Evidence Preserved
```

### 4. Timesheet Entry

```
Clock In (GPS) → Work Day → Clock Out (GPS) → Submit for Approval
```

### 5. QA Checklist

```
Select Checklist Type → Complete Items → Take Photos → Get Sign-off → Submit
```

---

## Mobile-First Design

All workflows optimized for phone:
- Large touch targets
- Minimal typing (select from lists)
- Quick camera access
- Offline support (V2)

---

## Key Screens

### Day Sheet Form (Mobile)

```
┌─────────────────────────┐
│ NEW DAY SHEET    [Save] │
├─────────────────────────┤
│ Job: [ABC Tower    ▼]   │
│ Date: [Today       📅]  │
│                         │
│ WORKERS      [+ Add]    │
│ John Smith   8 hrs      │
│ Mike Jones   8 hrs      │
│                         │
│ DESCRIPTION             │
│ ┌─────────────────────┐ │
│ │ Waterproofing prep  │ │
│ │ work to basement... │ │
│ └─────────────────────┘ │
│                         │
│ [Get Client Signature]  │
└─────────────────────────┘
```

### Client Signature

```
┌─────────────────────────┐
│ CLIENT SIGN-OFF         │
├─────────────────────────┤
│ ABC Tower - 8 Dec 2024  │
│ Workers: John, Mike     │
│ Hours: 16 total         │
│                         │
│ ┌─────────────────────┐ │
│ │                     │ │
│ │   [Signature Pad]   │ │
│ │                     │ │
│ └─────────────────────┘ │
│                         │
│ Client Name: __________ │
│ 📍 123 Main St (GPS)   │
│ 🕐 15:32 AEDT          │
│                         │
│ [Confirm & Save]        │
└─────────────────────────┘
```

---

## Success Metrics

| Metric | Target |
|--------|--------|
| Day sheet capture | < 2 minutes |
| Sign-off rate | 100% before submit |
| Timesheet accuracy | GPS verified |
| QA completion | By end of week |

---

## Pain Points Solved

| Before | After |
|--------|-------|
| Paper day sheets | Digital capture |
| Lost sign-offs | GPS + timestamp evidence |
| End-of-week rush | Real-time capture |
| Illegible handwriting | Structured data |
| Tickets in wallets | Centralized tracking |

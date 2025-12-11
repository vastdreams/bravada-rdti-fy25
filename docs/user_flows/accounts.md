# User Flow: Accounts

> **Persona**: Accounts / Finance / Admin  
> **Primary Modules**: Billing & Invoicing, Suppliers & POs, BI

---

## Role Summary

Manages billing, payments, and financial tracking.

| Responsibility | Module |
|----------------|--------|
| Create invoices | Billing & Invoicing |
| Track payments | Billing & Invoicing |
| Manage suppliers | Suppliers & POs |
| Financial reports | BI & Reporting |

---

## Key Workflows

### 1. Progress Claim Creation

```
End of Period → Create Claim → Calculate Work Value → Add Approved Variations → Calculate Retention → Submit to PM for Review → Send to Client
```

| Component | Calculation |
|-----------|-------------|
| Work Value | % complete × Contract value |
| Variations | Sum(approved variation values) |
| Less Previous | Prior claims |
| Less Retention | Per contract % |
| = This Claim | Net claimable |

### 2. Variation Invoice

```
Variation Approved → Create Invoice → Attach Evidence (day sheets, emails) → Send
```

### 3. Payment Tracking

```
Invoice Sent → Track Due Date → Receive Payment → Mark Paid → Reconcile
```

### 4. Supplier Bill Processing

```
Bill Received → Match to Job → Classify Category → Approve → Schedule Payment
```

| Category | Examples |
|----------|----------|
| Materials | Product suppliers |
| Subcontractor | Trade invoices |
| Plant | Equipment hire |
| Other | Permits, testing |

### 5. Purchase Order

```
PM Requests → Create PO → Send to Supplier → Track Delivery → Match to Bill
```

---

## Aging Report

```
CURRENT     1-30 DAYS    31-60 DAYS    61-90 DAYS    >90 DAYS
$125,000    $85,000      $45,000       $25,000       $188,000
    ✓          ✓            ⚠             ⚠            🔴
```

### Collection Actions

| Age | Action |
|-----|--------|
| 30+ days | Send reminder |
| 60+ days | Phone call |
| 90+ days | Escalate |

---

## Cash Flow View

```
WEEK         INFLOWS      OUTFLOWS     NET          BALANCE
Dec 9-15     $107,800     $85,000      +$22,800     $267,800
Dec 16-22    $45,200      $92,000      -$46,800     $221,000
Dec 23-29    $0           $45,000      -$45,000     $176,000
Dec 30-Jan 5 $185,000     $110,000     +$75,000     $251,000
```

---

## Success Metrics

| Metric | Target |
|--------|--------|
| Invoice turnaround | < 48 hours after period end |
| DSO (Days Sales Outstanding) | < 45 days |
| Claim disputes | < 5% |
| Payment accuracy | 100% |

---

## Pain Points Solved

| Before | After |
|--------|-------|
| Manual claim calculation | Automated from job data |
| Lost evidence | Attached to invoice |
| Aging in spreadsheet | Real-time dashboard |
| Supplier bills untracked | Matched to jobs |
| Cash flow guessing | Forecast from data |

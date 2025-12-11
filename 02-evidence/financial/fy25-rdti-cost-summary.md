# PATH: 02-evidence/financial/fy25-rdti-cost-summary.md
# PURPOSE:
# - Comprehensive financial summary extracted from FY25 BRAVADA R&D Working spreadsheet.
# - Documents all R&D costs, employee allocations, and supporting calculations.
#
# ROLE IN ARCHITECTURE:
# - Financial evidence layer: provides cost justification for RDTI claim.
#
# MAIN EXPORTS:
# - Employee R&D cost allocations
# - Overhead and subscription allocations
# - Total R&D expenditure summary
#
# NON-RESPONSIBILITIES:
# - Does NOT contain original source files (see Info_Files/)
# - Does NOT contain timesheet details (see time-records/)
#
# NOTES FOR FUTURE AI:
# - Data extracted from: FY25 BRAVADA R&D Working FY 24-25.xlsx
# - All amounts in AUD
# - R&D Refund calculated at 43.5% of allocated R&D expenses

---

# FY25 RDTI Cost Summary

## Filing Information

| Field | Value |
|-------|-------|
| **Company** | Bravada Group Pty Ltd |
| **Period** | 1 July 2024 to 30 June 2025 |
| **Project** | Quotech - AI-Driven Labor Efficiency and Quoting Analysis |
| **R&D Refund Rate** | 43.5% |
| **Source Document** | FY25 BRAVADA R&D Working FY 24-25.xlsx |

---

## Summary Totals

| Category | Total Expense | Allocated R&D | R&D Refund (43.5%) |
|----------|---------------|---------------|---------------------|
| **Payroll (8 employees)** | $1,112,579.96 | $520,412.60 | $226,379.48 |
| **Contractor (FSE Research)** | $187,425.36 | $187,425.36 | $81,530.03 |
| **Property Rent** | $87,697.40 | $21,924.35 | $9,537.09 |
| **IT & Subscriptions** | $164,217.33 | $41,656.88 | $18,120.74 |
| **GRAND TOTAL** | **$1,551,919.99** | **$771,419.19** | **$335,567.35** |

---

## Employee Payroll Allocations

### R&D Team Members

| # | Employee | Role | Earnings | Super | Total | R&D % | Allocated R&D | R&D Refund |
|---|----------|------|----------|-------|-------|-------|---------------|------------|
| 1 | Andrew Milan | R&D Manager | $143,520.31 | $16,489.23 | $160,009.54 | 40% | $64,003.82 | $27,841.66 |
| 2 | Gary McMahon | Managing Director | $188,444.35 | $21,671.11 | $210,115.46 | 60% | $126,069.28 | $54,840.14 |
| 3 | Kishan Antony | Estimation Module Design Lead | $99,207.88 | $11,285.00 | $110,492.88 | 75% | $82,869.66 | $36,048.30 |
| 4 | Lance Donald | PM Module Lead | $118,296.00 | $12,565.08 | $130,861.08 | 20% | $26,172.22 | $11,384.91 |
| 5 | Luba Levieva | Accounts Module Lead | $110,333.00 | $12,688.06 | $123,021.06 | 40% | $49,208.42 | $21,405.66 |
| 6 | Steven Baker | Operational User Design Reviewer | $131,265.50 | $14,901.24 | $146,166.74 | 20% | $29,233.35 | $12,716.51 |
| 7 | Tim McMahon | Operational User Design Reviewer | $133,120.00 | $15,308.80 | $148,428.80 | 40% | $59,371.52 | $25,826.61 |
| 8 | Angelica Costeletos | Implementation Co-ordinator | $74,874.00 | $8,610.34 | $83,484.34 | 100% | $83,484.34 | $36,315.69 |

**Payroll Subtotal**: $520,412.60 allocated | $226,379.48 refund

---

## Employee R&D Activities

### Andrew Milan - R&D Manager (40% allocation)
- Project design including interface between Quote system / SimPro / Xero & Quotech
- Testing & sense checking to project actuals
- Instructions for / meetings with Quotech Program Designers
- Attend meetings with Project Team & Quotech Program Designers

### Gary McMahon - Managing Director (60% allocation)
- Project development, planning & management
- Management Report design & delivery
- External consultant engagement & contracts management
- Attend meetings with Project Team & Quotech Program Designers

### Kishan Antony - Estimation Module Design Lead (75% allocation)
- Interface for delivery of Quoting System data into Quotech
- Project mapping & process changes for loading of Quote KPI's
- Subsequent changes to Quote versions or addition of Quote variations
- Manual loading of Quote KPI's into Quotech during development phase until uploads can be automated

### Lance Donald - PM Module Lead (20% allocation)
- Custodian of Quoting System
- Responsible for redesign of Quoting system to accommodate ready transfer of Quote Data Fields into Quotech
- Ongoing redesign / upgrading of Quoting System to accommodate demands / requirements of business

### Luba Levieva - Accounts Module Lead (40% allocation)
- Primary responsibility for internal processes to facilitate recording of Job specific costs into XERO
- Works with internal stakeholders & Quotech Program Designers around changes to XERO data capture & recording
- Facilitates data transfer into Quotech
- Instructions for / meetings with Quotech Program Designers

### Steven Baker - Operational User Design Reviewer (20% allocation)
- Key Stakeholder for review & actioning of Quotech functionality / reporting when completed
- Participates in design of Job Performance management reporting systems
- Accommodates Field Team manager / supervisor requirements
- Field testing of On Site receipt & interpretation (incl hardware systems) of data delivered by simPRO & Quotech

### Tim McMahon - Operational User Design Reviewer (40% allocation)
- Custodian of simPRO Job Management System
- Redesign / alignment of simPRO functionality / data fields to align with Quotech data capture & reporting requirements
- Consultation with simPRO re changes / additional functionality required to simPRO platform for Quotech purposes
- Instructions for / meetings with Quotech Program Designers

### Angelica Costeletos - Implementation Co-ordinator (100% allocation)
- Full-time R&D implementation coordination
- [Specific activities to be documented]

---

## Contractor Costs

| Contractor | Service | Total | R&D % | Allocated R&D | R&D Refund |
|------------|---------|-------|-------|---------------|------------|
| FSE Research | Sub-Contracted R&D | $187,425.36 | 100% | $187,425.36 | $81,530.03 |

**Description**: Sub-Contracted Research and Development Works

---

## Property Rent Allocation (25% R&D)

| Item | Total | R&D % | Allocated R&D | R&D Refund |
|------|-------|-------|---------------|------------|
| Property Rent | $62,779.45 | 25% | $15,694.86 | $6,827.27 |
| Body Corporate | $7,200.00 | 25% | $1,800.00 | $783.00 |
| Cleaning | $7,540.00 | 25% | $1,885.00 | $819.98 |
| Electricity | $3,171.82 | 25% | $792.96 | $344.94 |
| Rates | $6,127.13 | 25% | $1,531.78 | $666.33 |
| Security Monitoring | $879.00 | 25% | $219.75 | $95.59 |
| **Total Rent** | **$87,697.40** | **25%** | **$21,924.35** | **$9,537.09** |

---

## IT & Subscriptions Allocation

| Category | Total | R&D % | Allocated R&D | R&D Refund |
|----------|-------|-------|---------------|------------|
| Subscriptions, Memberships, Licences | $29,513.63 | Manual | $2,149.07 | $934.85 |
| Telecommunications | $9,032.99 | 20% | $1,806.60 | $785.87 |
| Subscriptions (IT Infrastructure) | $125,670.71 | 30% | $37,701.21 | $16,400.03 |
| **Total IT & Subscriptions** | **$164,217.33** | - | **$41,656.88** | **$18,120.74** |

### Detailed Subscription Transactions

#### Computer Support ($20,951.20 total)
- Computer Troubleshooters - SOPHOS: $7,750
- Monthly IT services (Jul 24 - Jun 25): Various maintenance and support

#### Website & Social Media ($9,000 total)
- Atmosphere Design - Steve B: $750/month × 12 months

#### Telecommunications ($1,806.60 allocated)
- Business ICT monthly services: ~$220/month

#### Subscriptions, Memberships, Licences ($2,149.07 allocated)
- Adobe subscriptions
- CM3 - General Purchase: $1,960
- Various software licenses

---

## Evidence Documentation

### Source Files
- **Primary Source**: `Info_Files/FY25 BRAVADA R&D Working FY 24-25.xlsx`
- **Sheets**:
  1. BG- R&D Exp 24-25 (Summary)
  2. BG-Weekly R&D Working 24-25 (Weekly breakdown)
  3. BG- R&D Xero JE (Journal Entries - 396 entries)
  4. Subscriptions, Memberships (Detail)
  5-12. Individual employee timesheets (8 employees, daily entries)

### Employee Timesheet Evidence
Each employee has daily timesheet records showing:
- Date
- Week Ending
- Regular Daily Hrs Worked (without R&D allocation)
- Overtime Daily Hrs Worked (without R&D allocation)
- Regular Daily Hrs Worked R&D Quotech
- Overtime Daily Hrs Worked R&D Quotech
- Total Daily Hrs Worked R&D Quotech
- Project/Job Code (Quotech)
- Position Title

### XERO Integration
- Separate Chart of Account (CoA) for Research payroll
- Journal entries aligned to timesheets
- 396 journal entries documented in Sheet 3

---

## Verification Checklist

- [x] Total R&D expenses calculated
- [x] Employee allocations documented with percentages
- [x] Employee R&D activities described
- [x] Contractor expenses included
- [x] Property rent allocation calculated
- [x] IT & Subscriptions allocated
- [x] Timesheet evidence available
- [x] XERO journal entries documented
- [ ] All expenses verified against invoices
- [ ] Timesheet totals reconciled to payroll

---

## Future Notes

- Reconcile weekly payroll calculations to annual totals
- Verify all subscription allocations have supporting rationale
- Consider documenting allocation methodology for audit purposes
- Link specific timesheet entries to R&D module activities where possible

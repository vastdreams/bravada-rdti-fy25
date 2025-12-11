# PATH: 02-evidence/time-records/timesheet-summary-fy25.md
# PURPOSE:
# - Summary of employee timesheets for FY25 RDTI claim.
# - Documents time allocation to Quotech R&D project.
#
# ROLE IN ARCHITECTURE:
# - Time records evidence layer: supports labor cost claims.
#
# MAIN EXPORTS:
# - Employee time allocations
# - Timesheet format documentation
# - Evidence location references
#
# NON-RESPONSIBILITIES:
# - Does NOT contain the actual timesheet data (see source file)
# - Does NOT contain payroll calculations (see financial/)
#
# NOTES FOR FUTURE AI:
# - Source data in: Info_Files/FY25 BRAVADA R&D Working FY 24-25.xlsx
# - Each employee has individual sheet with daily time entries
# - Timesheet period: 1 July 2024 to 30 June 2025

---

# FY25 Timesheet Summary

## Overview

| Field | Value |
|-------|-------|
| **Period** | 1 July 2024 to 30 June 2025 |
| **Project** | Quotech - AI-Driven Labor Efficiency and Quoting Analysis |
| **Total Employees with Timesheets** | 8 |
| **Source File** | Info_Files/FY25 BRAVADA R&D Working FY 24-25.xlsx |

---

## Employees with R&D Time Allocations

| Employee | Position | R&D Allocation | Sheet in Workbook |
|----------|----------|----------------|-------------------|
| Andrew Milan | R&D Manager | 40% | " Andrew Milan" |
| Gary McMahon | Managing Director | 60% | " Gary McMahon " |
| Kishan Antony | Estimation Module Design Lead | 75% | " Kishan Antony " |
| Lance Donald | PM Module Lead | 20% | " Lance Donald " |
| Luba Levieva | Accounts Module Lead | 40% | " Luba Levieva " |
| Steven Baker | Operational User Design Reviewer | 20% | " Steven Baker " |
| Tim McMahon | Operational User Design Reviewer | 40% | " Tim McMahon " |
| Angelica Costeletos | Implementation Co-ordinator | 100% | " Angelica Costeletos " |

---

## Timesheet Data Format

Each employee timesheet contains daily entries with the following columns:

| Column | Description |
|--------|-------------|
| Employee | Employee name |
| Date | Daily date (YYYY-MM-DD) |
| Week Ending | Week grouping (e.g., "1st Week of Jul 24") |
| Regular Daily Hrs Worked without R&D Allocation | Normal business hours |
| Overtime Daily Hrs Worked without R&D Allocation | Overtime hours |
| Total Daily Hrs Worked without R&D Allocation | Total non-R&D hours |
| Regular Daily Hrs Worked R&D Quotech | Regular R&D hours |
| Overtime Daily Hrs Worked R&D Quotech | Overtime R&D hours |
| Total Daily Hrs Worked R&D Quotech | Total R&D hours |
| Project/Job Code | "Quotech" |
| Position Title | Employee's R&D role |
| Remarks | Additional notes |

---

## Sample Data (Andrew Milan - First Week of July 2024)

| Date | Total Hrs | R&D Hrs | Project | Position |
|------|-----------|---------|---------|----------|
| 2024-07-01 | 8 | 3 | Quotech | R&D Manager |
| 2024-07-02 | 7.6 | 5 | Quotech | R&D Manager |
| 2024-07-03 | 8 | 3 | Quotech | R&D Manager |
| 2024-07-04 | 8 | 4 | Quotech | R&D Manager |
| 2024-07-05 | 8 | 3 | Quotech | R&D Manager |
| 2024-07-06 | 0 | 0 | Quotech | R&D Manager |
| 2024-07-07 | 0 | 0 | Quotech | R&D Manager |

**Week 1 Total**: 39.6 hrs worked, 18 hrs R&D (45.5% of week)

---

## Evidence Structure

### Source Workbook Sheets
Each employee sheet contains approximately 365 daily entries:

1. **Andrew Milan** - 372 rows × 14 columns
2. **Gary McMahon** - 372 rows × 13 columns
3. **Kishan Antony** - 372 rows × 13 columns
4. **Lance Donald** - 372 rows × 13 columns
5. **Luba Levieva** - 376 rows × 13 columns
6. **Steven Baker** - 372 rows × 13 columns
7. **Tim McMahon** - 372 rows × 13 columns
8. **Angelica Costeletos** - 372 rows × 13 columns

### Weekly Summary
Sheet "2. BG-Weekly R&D Working 24-25" provides:
- Weekly aggregated payroll by employee
- 71 columns covering all weeks in FY25
- Row totals for verification

---

## XERO Integration

- Timesheets are aligned with XERO payroll entries
- Separate Chart of Account (CoA) "Research" for R&D payroll
- Journal entries in Sheet "3. BG- R&D Xero JE" (396 entries)

---

## Verification Checklist

- [x] All 8 employees have individual timesheet sheets
- [x] Daily entries with R&D hour breakdown
- [x] Project code consistently marked as "Quotech"
- [x] Position titles documented
- [x] Weekly summary available for reconciliation
- [ ] Total R&D hours reconciled to payroll calculations
- [ ] Timesheet approval signatures (if applicable)

---

## Future Notes

- Consider extracting monthly R&D hour totals per employee
- Create pivot table summary of R&D hours by week/month
- Verify timesheet hours match payroll calculations
- Document any overtime R&D hours specifically

# PATH: README.md
# PURPOSE:
# - Main entry point and overview for Bravada's RDTI (Research and Development Tax Incentive) filing project.
# - Provides navigation guide to all project documentation, evidence, and filing materials.

# ROLE IN ARCHITECTURE:
# - Project documentation root: serves as the index and guide for the entire RDTI filing process.

# MAIN EXPORTS:
# - Project structure overview
# - Navigation guide to all sections
# - Filing process workflow

# NON-RESPONSIBILITIES:
# - This file does NOT contain actual filing documents or evidence
# - Does NOT store sensitive financial or proprietary information

# NOTES FOR FUTURE AI:
# - When adding new documents, update the relevant section README
# - Maintain chronological order in evidence folders (use YYYY-MM-DD prefixes)
# - Never commit sensitive financial data or personal information to version control

---

# Bravada RDTI Filing Project - FY25

## 🌐 Hosted Application

| Resource | URL |
|----------|-----|
| **Live Website** | http://3.25.175.69 |
| **RDTI Application** | http://3.25.175.69/rdti-fy25-application.html |
| **GitHub Repository** | https://github.com/vastdreams/bravada-rdti-fy25 |

### Branches
- `main` - Production (deployed to EC2)
- `develop` - Development

---

## 🟢 FY25 FILING STATUS: DOCUMENTATION COMPLETE

| Document | Status | Location |
|----------|--------|----------|
| Application Content | ✅ Complete | `03-filing-documents/FY25-RDTI-Application-Content.md` |
| **Core Activities (Full)** | ✅ Complete | `03-filing-documents/FY25-Core-Activities-Complete.md` |
| Research Journal | ✅ Complete | `02-evidence/research-notes/FY25-Research-Journal.md` |
| Existing Knowledge Search | ✅ Complete | `02-evidence/research-notes/FY25-Existing-Knowledge-Search.md` |
| Evidence Index | ✅ Complete | `02-evidence/EVIDENCE-INDEX-FY25.md` |
| Financial Evidence | ✅ Verified | Xero & Excel reconciled ($771,419.27) |
| Employee Count | ✅ Verified | ~50 FTE (12 payroll + contractors, est. from OpEx) |
| Aggregated Turnover | ✅ Verified | $12,760,872.01 (Xero P&L) |
| Taxable Income | ✅ Verified | $195,852.07 profit (Xero P&L) |

### Core R&D Activities Registered
| Activity | Reference | FY25 Spend |
|----------|-----------|------------|
| Email/Document Context Intelligence | PQYAQTS17 | $385,710 |
| Quote Intelligence & Cost Analysis | P1SHYTK8Z | $385,709 |
| **Total** | - | **$771,419** |

---

## Overview

This repository contains all documentation, evidence, and filing materials for **Bravada Group's** Research and Development Tax Incentive (RDTI) claim for **Financial Year 2025**.

### Primary R&D Project
**Quotech: AI-Driven Labor Efficiency and Quoting Analysis**
- 5 AI-Driven Agentic Modules for Construction Sub-Contracting
- **R&D Expenditure (FY25)**: $771,419.27 (Xero verified ✅)
- **Expected R&D Refund**: $335,567.38 (at 43.5%)
- **Total Project Budget**: $5,500,000 (over project life to 2030)
- Duration: July 2022 - June 2030

## Company Information

| Field | Value |
|-------|-------|
| **Company** | Bravada Group |
| **Taxable Position** | $195,852.07 (profit) |
| **Aggregated Turnover** | $12,760,872.01 |
| **R&D Location** | Ringwood, VIC 3134 |

## Project Structure

```
RDTI Bravada/
├── 01-project-documentation/    # Project plans, scope, and administrative docs
│   ├── quotech-ai-driven-labor-efficiency.md  # Main project documentation
│   └── compliance-tracker.md    # Compliance pack status tracking
├── 02-evidence/                 # All supporting evidence for RDTI claim
│   ├── technical/               # Code, designs, research notes
│   ├── financial/               # XERO exports, invoices, costs
│   ├── time-records/            # Timesheets, payroll aligned to Research CoA
│   └── meetings-notes/          # Meeting notes, project discussions
├── 03-filing-documents/         # Completed forms, submissions, correspondence
├── 04-supporting-materials/     # Additional supporting documentation
│   ├── contracts/               # University, CSIRO, internship agreements
│   ├── patents/                 # Patent applications, IP documentation
│   └── publications/            # Pre-prints, market research reports
├── 05-templates/                # Reusable templates and checklists
├── 06-archive/                  # Previous filings, historical documents
└── Info_Files/                  # Raw data staging (incoming dumps)
```

## Quick Start

1. **Review Compliance Tracker**: Check `01-project-documentation/compliance-tracker.md` for outstanding items
2. **Review Project Documentation**: See `01-project-documentation/quotech-ai-driven-labor-efficiency.md`
3. **Upload Evidence**: Organize materials in `02-evidence/` subdirectories
4. **Track Progress**: Update compliance tracker as documents are added

## Key Dates

| Milestone | Date |
|-----------|------|
| **Filing Period** | FY25 (1 July 2024 - 30 June 2025) |
| **Submission Deadline** | ~April 2026 (10 months post FY end) |
| **Project Start Date** | July 2022 |
| **Project End Date** | June 2030 |

## The Five AI Modules (Quotech)

1. **Email and Directory AI** - Email categorisation, context mapping, directory creation
2. **Document Fetch and Information AI** - Micro-agentic chat interface for document retrieval
3. **Billing/PO/Invoice Intelligence** - Bill categorisation, PO matching, price intelligence
4. **Quote Intelligence** - KPI generation from estimation sheets, BI with chat interface
5. **Timesheet Planning** - Calendar resource planning, capacity intelligence

## Team & Contacts

| Role | Name | Email |
|------|------|-------|
| **Project Lead / Chair** | Abhishek Sehgal | abhishek.sehgal@bravada.com.au |
| **Documentation Lead** | Vibhuti Rajpal | - |
| **Tax Advisor** | Chander Ji | - |

**Bravada Group**
- Phone: 03 9872 3333 | Mobile: 04 1578 0001
- Address: Unit 3 / 10 Pilgrim Court, Ringwood, VIC, 3134
- Postal: PO Box 377, Vermont, VIC, 3133
- Website: www.bravada.com.au

## Documentation Standards

- All documents dated (YYYY-MM-DD format in filenames)
- Descriptive filenames indicating content
- XERO Research CoA used for R&D payroll tracking
- Version control for important documents
- Never include sensitive personal information in filenames

---

## Future Notes

- Consider automating evidence collection from development tools (Git, Jira, etc.)
- Set up regular reminders for documentation updates
- Establish clear criteria for what qualifies as R&D evidence
- Create automated checks for required documentation completeness

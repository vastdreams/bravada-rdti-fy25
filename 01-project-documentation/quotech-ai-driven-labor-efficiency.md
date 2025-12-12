# PATH: 01-project-documentation/quotech-ai-driven-labor-efficiency.md
# PURPOSE:
# - Core project documentation for the Quotech "AI-Driven Labor Efficiency and Quoting Analysis" R&D project.
# - Primary project for Bravada's FY25 RDTI claim.
#
# ROLE IN ARCHITECTURE:
# - Project documentation layer: defines the R&D activities, objectives, and scope for RDTI filing.
#
# MAIN EXPORTS:
# - Project specifications and objectives
# - Technical uncertainty statements
# - 5 AI Module descriptions
#
# NON-RESPONSIBILITIES:
# - Does NOT contain financial evidence (see 02-evidence/financial/)
# - Does NOT contain timesheets (see 02-evidence/time-records/)
#
# NOTES FOR FUTURE AI:
# - This is the PRIMARY R&D project for FY25 filing
# - Each module can be documented separately if needed
# - Link all evidence to specific modules where possible

---

# Quotech: AI-Driven Labor Efficiency and Quoting Analysis

## Filing Information

| Field | Value |
|-------|-------|
| **Project Name** | AI-Driven Labor Efficiency and Quoting Analysis |
| **Project Reference** | Q (Quotech) |
| **Filing Year** | FY25 (Financial Year ending 30 June 2025) |
| **Total R&D Expenditure** | $771,419.27 (Xero verified) |
| **Expected R&D Refund** | $335,567.38 (at 43.5%) |
| **Expected Total Spend** | $5,500,000 (over project life to 2030) |
| **Project Duration** | July 2022 to June 2030 |
| **R&D Location** | 3134 (Ringwood, VIC, Australia) |

## Company Information

| Field | Value |
|-------|-------|
| **Company** | Bravada Group Pty Ltd |
| **Taxable Income/Loss** | -$290,000 (loss position) |
| **Aggregated Turnover** | $9,016,000 |
| **Total Gross Expenses (FY25)** | $1,551,919.99 |
| **Export Revenue** | [To be confirmed] |
| **Total Employees (30 Jun 2024)** | [To be confirmed] |
| **R&D Employees** | 8 internal + 1 contractor |

---

## Executive Summary

The Quotech project focuses on researching and developing AI-Driven Agentic Modules to address operational gaps for Construction Sub-Contracting Companies. The platform aims to create AI-powered Business Intelligence (BI) and Planning capabilities through five interconnected modules.

---

## Technical Objectives

### Primary Objective
Develop AI-driven agentic systems that can autonomously handle complex business operations for construction sub-contracting companies, including email management, document retrieval, billing intelligence, quoting analysis, and resource planning.

### Secondary Objectives
- Create micro-agentic architectures for modular AI functionality
- Integrate with existing business systems (email, documents, accounting)
- Develop natural language chat interfaces for business intelligence
- Build predictive capacity planning and resource optimization

---

## The Five AI-Driven Agentic Modules

### Module 1: Email and Directory AI Module
**Purpose**: Integrate Email categorisation and context map, alongside document directory creation.

**Technical Scope**:
- Email classification and categorisation algorithms
- Context mapping between emails and projects
- Automated directory structure creation
- Entity extraction and relationship mapping

**Technical Uncertainty**:
- How to accurately categorise construction-specific emails without extensive training data
- Methods for creating meaningful context maps across diverse email threads
- Automated directory organization that adapts to varying project structures

---

### Module 2: Document Fetch and Information AI
**Purpose**: Chat interface using micro-agentic structure for fetching information from general category data.

**Technical Scope**:
- Micro-agentic architecture design
- Natural language query processing
- Multi-source document retrieval
- Information synthesis and response generation

**Technical Uncertainty**:
- Optimal micro-agent coordination for complex queries
- Retrieval accuracy across heterogeneous document formats
- Context preservation in multi-turn conversations
- Handling construction-specific terminology and abbreviations

---

### Module 3: Billing / PO / Invoice Intelligence
**Purpose**: W. Emails - categorise bills against POs and supplier data with price intelligence and approvals.

**Technical Scope**:
- Invoice parsing and data extraction
- PO matching algorithms
- Supplier data integration
- Price variance detection and intelligence
- Approval workflow automation

**Technical Uncertainty**:
- Accurate matching of invoices to POs with incomplete or inconsistent data
- Price intelligence models for construction materials with volatile pricing
- Automated approval decision logic with appropriate confidence thresholds

---

### Module 4: Quote Intelligence
**Purpose**: Use quoted estimation Excel sheets to generate KPIs with cost centers and data integration for detailed BI for reporting with Chat Auto-Intelligence.

**Technical Scope**:
- Excel estimation sheet parsing and analysis
- KPI generation algorithms
- Cost center allocation models
- BI dashboard integration
- Conversational analytics interface

**Technical Uncertainty**:
- Parsing diverse Excel estimation formats without standardization
- Meaningful KPI generation from incomplete historical data
- Real-time cost center analysis with varying project structures
- Natural language querying of complex business intelligence data

---

### Module 5: Timesheet Planning
**Purpose**: Calendar resource planning AI interface for logging and reminders, alongside capacity intelligence.

**Technical Scope**:
- Resource scheduling algorithms
- Capacity forecasting models
- AI-assisted time logging
- Smart reminder systems
- Utilization analytics

**Technical Uncertainty**:
- Predictive capacity planning with variable project demands
- Optimal resource allocation across competing projects
- Learning individual work patterns for intelligent suggestions
- Integration with existing calendar and project management systems

---

## Systematic Investigation Approach

1. **Literature Review**: Analysis of existing AI/ML approaches for construction industry applications
2. **Prototype Development**: Iterative development of each module with hypothesis testing
3. **Integration Testing**: Systematic testing of module interactions and data flows
4. **User Validation**: Structured feedback collection and iteration cycles
5. **Performance Optimization**: Systematic improvement based on measured outcomes

---

## Technical Advancement

This project advances knowledge in:
- **Agentic AI Architecture**: Novel micro-agentic structures for business applications
- **Construction Domain AI**: Industry-specific AI applications for sub-contracting workflows
- **Multi-Modal Integration**: Combining email, document, financial, and scheduling data
- **Conversational BI**: Natural language interfaces for complex business intelligence

---

## Evidence References

### Technical Evidence
- [ ] Code Repository: GitHub screenshots for Quotech (`02-evidence/technical/`)
- [ ] Architecture Documentation (`02-evidence/technical/`)
- [ ] Research Experiment Setup (`02-evidence/technical/`)
- [ ] Research Notes (`02-evidence/technical/`)

### Financial Evidence
- [x] XERO Research CoA Records - 396 journal entries documented
- [x] Detailed Working and Expenses (`Info_Files/FY25 BRAVADA R&D Working FY 24-25.xlsx`)
- [x] Cost Summary (`02-evidence/financial/fy25-rdti-cost-summary.md`)

### Time Records
- [x] Timesheets - 8 employees with daily entries (`Info_Files/FY25 BRAVADA R&D Working FY 24-25.xlsx`)
- [x] Weekly R&D Working breakdown included
- [x] Timesheet Summary (`02-evidence/time-records/timesheet-summary-fy25.md`)

### Supporting Materials
- [ ] University Agreements (`04-supporting-materials/contracts/`)
- [ ] CSIRO Agreements (`04-supporting-materials/contracts/`)
- [ ] PhD Meeting Documentation (`04-supporting-materials/contracts/`)
- [ ] Pre-print Publications (`04-supporting-materials/publications/`)
- [ ] Market/Research Landscape Report (`04-supporting-materials/publications/`)
- [ ] Internship Agreements (`04-supporting-materials/contracts/`)

---

## Team

- **Project Lead / Chair**: Abhishek Sehgal
- **Documentation Lead**: Vibhuti Rajpal
- **Tax Advisor**: Chander Ji
- [Additional team members to be added]

---

## Key Contacts

**Bravada Group**
- Email: abhishek.sehgal@bravada.com.au
- Phone: 03 9872 3333
- Mobile: 04 1578 0001
- Address: Unit 3 / 10 Pilgrim Court, Ringwood, VIC, 3134
- Postal: Post Office Box 377, Vermont, VIC, 3133
- Website: www.bravada.com.au

---

## Future Notes

- Consider documenting each module as a separate sub-project if complexity warrants
- Establish clear mapping between module development phases and R&D costs
- Create automated evidence collection from development tools
- Link timesheet entries to specific module work where possible

# PATH: 03-filing-documents/FY25-RDTI-Application-Content.md
# PURPOSE:
# - Complete FY25 RDTI Application content ready for submission
# - All sections formatted to match AusIndustry requirements
#
# ROLE IN ARCHITECTURE:
# - Primary filing document for FY25 R&D Tax Incentive application
#
# MAIN EXPORTS:
# - Project overview, Core Activities, Hypotheses, Experiments, Evaluation, Conclusions
#
# NOTES FOR FUTURE AI:
# - This document follows the successful FY23/FY24 pattern but with stronger technical detail
# - All content must be consistent with evidence in 02-evidence/ and core activity documents

---

# R&D Tax Incentive Application - FY25

## Application Details

| Field | Value |
|-------|-------|
| **Company Name** | BRAVADA GROUP PTY LTD |
| **ABN** | 58167664815 |
| **ACN** | 167664815 |
| **Income Period** | 01 Jul 2024 - 30 Jun 2025 |
| **Financial Year** | 2024-25 |

---

## Registration Type

**Is the company registered with ASIC?**  
☑ Yes, under an Australian law

**Registration Date**: 22/01/2014

**Is the company the head of a consolidated group?**  
☐ Yes  
☑ No, the company is not part of a consolidated or multiple entry consolidated group

**Is the company controlled by tax exempt entities?**  
☐ Yes  
☑ No

**Does the company have an Ultimate Holding Company?**  
☑ Yes

| Field | Value |
|-------|-------|
| Company Name | PHOENIX EQUITY INVESTMENTS PTY LTD |
| ABN | 39677010043 |
| ACN | 677010043 |
| Country | AUSTRALIA |

---

## Company Details

**ANZSIC Division**: E - CONSTRUCTION

**ANZSIC Class**: 3299 Other Construction Services n.e.c.

---

## Contact Details

### Primary Company Contact

| Field | Value |
|-------|-------|
| Title | Mr |
| First Name | Gary |
| Last Name | McMahon |
| Position | CEO |
| Phone | 0419546264 |
| Email | gary.mcmahon@bravada.com.au |
| Main Business Address | Unit 3 10 Pilgrim Ct, RINGWOOD VIC 3134 |
| Website | www.bravada.com.au |

### Tax Agent Contact

| Field | Value |
|-------|-------|
| Title | Mr |
| First Name | Chander |
| Last Name | Dhawan |
| Position | Advisor |
| Tax Agent Registration | 78394004 |
| Phone | 0421820275 |
| Email | cdhawanca@gmail.com |
| Tax Agent ABN | 67584245145 |
| Tax Agent Name | The Trustee for CAMA FAMILY TRUST |

---

## Application Inclusions

**This application will include:**  
☑ None of the above (no advance findings, RSPs, CRCs, or collaborative agreements)

**Will the company include activities excluded from being a core activity?**  
☐ Yes, as supporting activities  
☑ No

---

## Employees

**Total number of employees at 30 Jun 2025**  
50 (estimated FTE including contractors; 12 payroll employees plus subcontractor FTE based on wages analysis)

**Number of employees engaged in R&D (person years / FTE)**  
8–10 FTE (we use 8 FTE for conservative reporting)

**Number of independent contractors engaged in R&D activities**  
2

**Notes on estimation approach:**  
Bravada is a construction group with a mix of payroll staff and subcontractors. Xero and the FY25 working file show:

- R&D wages (account 434): $520,412.60  
- R&D contracted services (account 415): $187,425.36

Using typical construction/technical salary bands and the documented R&D time allocations in the Excel workings, this maps to roughly **8–10 FTE** engaged on eligible R&D in FY25 (about 6 FTE from wages and 2–4 FTE equivalent from contractors). For the purposes of this form we report **8 FTE** employees and **2** R&D contractors.

---

## Finance

| Field | Value |
|-------|-------|
| **Taxable Income/Loss** | AUD 195,852.07 (Profit) |
| **Aggregated Turnover** | AUD 12,760,872.01 |
| **Export Revenue** | AUD 0.00 |

*Figures are drawn from the Xero Profit & Loss report for the period 1 Jul 2024 – 30 Jun 2025. R&D expenditure reconciles to the dedicated R&D accounts in Xero and to the FY25 Excel working file.*

---

# PROJECT DETAILS

## Project Name

**Quotech: AI-Driven Labor Efficiency and Quoting Analysis System**

**Project ID**: PBN3C99CP (continuation from FY23/FY24)  
**Project Reference**: QUO0001

---

## Project Duration

**Jul 2022 to Jun 2026**

---

## Total Project Budget

**AUD 1,500,000.00**  
(R&D and non-R&D expenses over the project life)

---

## Project Objectives (portal: “What are the objectives of this project?”)

The objective of this project is to build **Quotech**, an AI‑driven operating layer for construction sub‑contractors that can finally make sense of the flood of emails, documents and quotes that run through a business, and turn them into live, trusted intelligence for planning and billing.

In simple terms, we are trying to answer two questions:

1. Can we build a context engine that actually understands a sub‑contractor’s world of jobs, POs, bills, quotes, day sheets and QA records well enough that staff can ask it questions and rely on the answers?
2. Can we turn the messy, inconsistent quotes and timesheets that arrive every day into structured cost and labour data that can drive honest margin analysis and better decisions, without drowning people in admin?

To do that, the project is split into **five AI‑driven modules**:

1. **Email and Directory AI Module** – classifies incoming emails and attachments into Bills, POs, Contracts, Variations, Day Sheets, QA records and general information, and files them against the right jobs and suppliers.
2. **Document Fetch and Information AI** – lets a user ask for documents or answers (“show all variations linked to PO 123”, “what is the latest subcontract agreement for Job X?”) and get grounded, explainable responses.
3. **Billing / PO / Invoice Intelligence** – reads supplier bills, matches them to POs, checks prices against history and tags them for approval with confidence scores.
4. **Quote Intelligence** – reads quotes in all their different formats, extracts structured items and cost centres, and feeds that into BI and forecasting so a sub‑contractor can see where margins are likely to blow out.
5. **Timesheet Planning** – brings calendar, day sheets and job budgets together to spot capacity issues and anomalies early.

Underneath these modules we are doing **foundational R&D** on two fronts:

- a **context and memory architecture** (Core Activity 1) that can live with construction documents over years and get better with use; and
- a **quote and cost intelligence engine** (Core Activity 2) that can turn supplier quotes into clean, analysable data.

The ultimate objective is not just to automate some admin, but to create a reusable technical backbone that sub‑contractors can trust when they ask “what is really going on in my jobs this week?”.

---

## Documents and records kept (portal: “Describe what documents you have kept…”) 

We keep detailed, contemporaneous records of the Quotech R&D work so that every major decision and experiment can be reconstructed later. These are maintained mainly in Notion, GitLab, Excel, and cloud storage, all with timestamps and version history where possible.

At a high level, our records include:

1. **Research notes and design documents**  
   - Architecture and design documents describing the context engine, classification modules and quote intelligence pipelines.
   - Research notes and pre‑print drafts setting out the theoretical background, hypotheses and validation strategies (including DREAM‑inspired context work).
   - Planning documents for each of the five modules, with milestones and data requirements.

2. **Code and experiment artefacts**  
   - GitLab repositories for `quotech-backend`, `quotech-frontend` and `billing-frontend`, including branches, merge requests and code review history.
   - Configuration files, scripts and notebooks used to run classification, retrieval, quote extraction and anomaly detection experiments.
   - Validation outputs: metrics tables, confusion matrices, latency benchmarks and comparison plots for different model versions.

3. **Data and pilot company records**  
   - Briefs describing the origin of pilot company datasets and the agreed de‑identification steps.
   - Results of benchmark runs on real data (emails, documents, quotes, timesheets), including summaries of issues found and fixes applied.
   - Notes from pilot sessions with operations staff and finance teams.

4. **Compliance and financial evidence**  
   - Timesheet summaries and R&D allocation notes for employees and contractors working on Quotech.
   - Invoices for R&D contractors, cloud compute, storage, and specialist software used to support the experiments.
   - Xero reports and the FY25 R&D working Excel file, including account‑level reconciliation to the R&D Chart of Accounts.

5. **Chain‑of‑thought and audit logs**  
   - COT logs for key AI decisions (particularly around classification and quote parsing), stored in a dedicated table so we can see how the system reasoned about borderline cases.
   - Change logs describing technical pivots (e.g. when we moved from a pure memory tree to the hybrid SQL + graph design) and why.

Together these records provide contemporaneous evidence of the experiments, their rationale, the results, and the conclusions we drew.

---

## Plant and facilities (portal: “Briefly describe the plant and facilities…”) 

Quotech is a software and data‑intensive project. The “plant and facilities” are mostly compute and network infrastructure rather than traditional factory equipment.

The main facilities are:

1. **Development machines and workstations**  
   Used by the development and research team for coding, data engineering, analysis and running smaller tests.

2. **On‑premise and cloud servers**  
   - Local servers used for internal test deployments of the Quotech backend, frontend and supporting services.
   - Cloud compute (primarily AWS EC2) used for heavier workloads such as embedding large document corpora, running batch experiments and hosting pilot environments.

3. **Databases and storage**  
   - PostgreSQL for structured data.
   - Neo4j for the context graph.
   - Vector database (ChromaDB) for semantic embeddings.
   - Object storage (e.g. S3) for documents, logs and model artefacts.

4. **AI/ML infrastructure**  
   - Access to LLM APIs (OpenAI, DeepSeek) for summarisation, classification and refinement experiments.
   - GPU‑enabled instances for training and evaluating ML models.
   - Monitoring, logging and tracing tools for observing behaviour in pilot deployments.

These facilities are used directly in the conduct of the R&D activities – in particular for running experiments, storing and querying large volumes of documents and logs, and simulating production loads for performance testing.

---

## Beneficiary details (portal: “To establish whether the Company will be a beneficiary…”) 

Bravada Group Pty Ltd is the main and direct beneficiary of the Quotech R&D activities.

### Ownership of results

All software, models and documentation produced under this project are created for and owned by Bravada Group, including:

- the Quotech platform (frontend and backend code);
- the context engine, classifiers and quote intelligence pipelines;
- the schemas, specifications and configuration used to drive the system; and
- the research notes, pre‑prints and internal design documents.

We work with contractors and pilot sub‑contractors under arrangements where Bravada retains IP in the platform and techniques, while pilot companies receive the benefit of the working system for their own operations.

### Control of R&D direction and conduct

Bravada controls the direction and conduct of all Quotech R&D. In practical terms this means we:

- decide which modules and hypotheses to prioritise in a given year;
- design the experiments and set acceptance thresholds;
- choose the technology stack and architecture; and
- decide when a line of work is ready to move from experiment to production or needs to be re‑designed.

External parties (e.g. pilot companies) provide domain input and feedback but do not control the R&D program.

### Financial burden

The financial burden of the R&D is borne by Bravada Group:

- R&D wages are paid by Bravada and recorded against dedicated R&D accounts in Xero.
- R&D contractor costs, cloud infrastructure, software subscriptions and other operating costs are funded by Bravada.
- There are no external grants or guarantees funding the Quotech R&D at this stage.

Any future commercial benefit from Quotech – whether as a product, service or licensing opportunity – will accrue to Bravada Group. The company is therefore carrying both the development risk and the potential reward.

---

## Field of Research

**ANZSRC Division**: 46 Information and Computing Sciences  
**ANZSRC Group**: 4602 Artificial intelligence

---

# CORE R&D ACTIVITIES – SUMMARY

For this project we are registering **two core R&D activities**:

1. **Email and Document Context Intelligence and Sub-Module Creation: Bills, Timesheets, BI and Information** (Reference: PQYAQTS17)
2. **AI-Driven Quote Reading, Cost Center Extraction and Predictive BI Analytics** (Reference: P1SHYTK8Z)

The detailed descriptions for each core activity (hypotheses, experiments, evaluation and conclusions) are set out in:

- `03-filing-documents/FY25-Core-Activities-Complete.md`

and map directly onto the fields in the AusIndustry portal.

At a high level:

- Core Activity 1 covers the **context engine and classification work** (including the modules for billing/PO intelligence and timesheet anomaly detection).
- Core Activity 2 covers the **quote and cost intelligence work** (including predictive BI and anomaly detection for pricing).

Both activities meet the definition of core R&D activities under s 355‑25(1) of the ITAA 1997: the outcomes could not be known in advance, the work follows a clear hypothesis–experiment–evaluation loop based on established AI/ML and software engineering principles, and the purpose is to generate new knowledge about how these techniques behave in the construction sub‑contractor domain.

---

*Document prepared: December 2024*  
*Last updated: [Date]*

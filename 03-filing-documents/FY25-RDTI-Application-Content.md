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
# - This document follows AusIndustry software guidance with technical uncertainty focus
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
☑ Yes, as supporting activities  
☐ No

*Note: Supporting activities include integration of experimental components into production modules (billing, timesheets, BI interfaces), UI development, and pilot deployment infrastructure. These are directly related to the core experimental work and would not have been conducted without it.*

---

## Employees

**Total number of employees at 30 Jun 2025**  
50 (estimated FTE including contractors; 12 payroll employees plus subcontractor FTE based on wages analysis)

**Number of employees engaged in R&D (person years / FTE)**  
8 FTE

**Number of independent contractors engaged in R&D activities**  
2

**Notes on estimation approach:**  
Bravada is a construction group with a mix of payroll staff and subcontractors. Xero and the FY25 working file show:

- R&D wages (account 434): $520,412.60  
- R&D contracted services (account 415): $187,425.36

Using typical construction/technical salary bands and the documented R&D time allocations in the Excel workings, this maps to approximately 8 FTE engaged on eligible R&D in FY25 (6 FTE from wages and 2 FTE equivalent from contractors).

---

## Finance

| Field | Value |
|-------|-------|
| **Taxable Income/Loss** | AUD 195,852.07 (Profit) |
| **Aggregated Turnover** | AUD 12,760,872.01 |
| **Export Revenue** | AUD 0.00 |
| **R&D Expenditure FY25** | AUD 771,419.00 |

*Figures are drawn from the Xero Profit & Loss report for the period 1 Jul 2024 – 30 Jun 2025. R&D expenditure reconciles to the dedicated R&D accounts in Xero and to the FY25 Excel working file.*

---

# PROJECT DETAILS

## Project Name

**Quotech: AI-Driven Labor Efficiency and Quoting Analysis System**

**Project ID**: PBN3C99CP (continuation from FY23/FY24)  
**Project Reference**: QUO0001

---

## Project Duration

**Jul 2022 to Jun 2030**

---

## Total Project Budget

**AUD 5,500,000.00**  
(Total eligible R&D expenditure over the project life, including prior years and anticipated future expenditure. The project is building a neurosymbolic AI capable of digesting 10,000+ documents with micro-agent orchestration for construction document intelligence.)

---

## Project Objectives (portal: "What are the objectives of this project?")

The objective of this project is to investigate and resolve specific technical uncertainties in the field of applied artificial intelligence and information retrieval, with application to construction sub-contractor document processing.

**Technical knowledge gap:**  
Existing techniques for document classification, semantic retrieval and structured data extraction (including retrieval-augmented generation, vector search, and transformer-based parsing) have been developed and tested primarily on general-purpose corpora such as Wikipedia, news articles and enterprise documents. It is not known whether these techniques, individually or in combination, can achieve the accuracy, latency and reliability thresholds required for real-time operational use on the heterogeneous, domain-specific document types that characterise construction sub-contracting (variations, day sheets, supplier quotes in inconsistent formats, QA records, etc.).

**Field of science/technology:**  
The experimental work sits within the field of Information and Computing Sciences (ANZSRC Division 46), specifically Artificial Intelligence (Group 4602). The project draws on techniques from information retrieval, natural language processing, graph-based knowledge representation, and supervised classification.

**Primary experimental questions:**

1. **Context and retrieval architecture**: Can a hybrid architecture combining graph-based document relationships, vector embeddings and usage-driven edge weighting achieve classification accuracy above 85% and retrieval latency below 500ms P95 on real construction document corpora?

2. **Quote parsing and cost extraction**: Can an OCR and model-based parsing pipeline reliably extract structured cost data from the variety of quote formats used by construction suppliers, with field-level accuracy above 90% for structured formats?

**Purpose:**  
The primary purpose of the experimental work is to generate new knowledge about how these AI and information retrieval techniques behave in the construction sub-contractor domain, and to determine the limits of their applicability. The resulting knowledge will inform both the Quotech platform and the broader field of domain-specific document intelligence.

**Modules:**  
The project is structured into functional modules that serve as testbeds for the core experiments:

1. **Email and document classification** – testbed for multi-signal classification experiments
2. **Document retrieval and context engine** – testbed for graph/vector hybrid retrieval experiments
3. **Quote parsing and cost extraction** – testbed for OCR, parsing and mapping experiments
4. **Anomaly and margin analysis** – testbed for threshold calibration and prediction experiments

Integration of experimental components into production-ready modules (billing workflows, timesheet validation, BI dashboards) is treated as **supporting R&D activity**, not core experimental work.

---

## Documents and records kept (portal: "Describe what documents you have kept…") 

We maintain detailed, contemporaneous records of the Quotech R&D work so that each experiment and decision can be reconstructed and substantiated. Records are primarily stored in Notion, GitLab, Excel workbooks and cloud storage, all with timestamps and version history.

**1. Prior art and existing knowledge search**  
- Documented searches of academic literature (arXiv, ACL Anthology, IEEE), patent databases, and commercial product documentation.
- Search terms, dates, sources reviewed, and conclusions about why existing solutions did not resolve the specific technical uncertainties.
- Meeting notes from consultations with AI engineers and construction software specialists.

**2. Research notes and experiment design**  
- Architecture and design documents for each experimental component (context engine, classifiers, quote parser).
- Written hypotheses with explicit acceptance criteria before experiments commenced.
- Experiment protocols specifying datasets, metrics, baselines and evaluation methods.

**3. Code and experiment artefacts**  
- GitLab repositories (`quotech-backend`, `quotech-frontend`, `billing-frontend`) with branches, merge requests and code review history.
- Configuration files, scripts and notebooks used to run experiments.
- Validation outputs: metrics tables, confusion matrices, latency benchmarks, plots comparing model versions.

**4. Data and pilot records**  
- Briefs describing the origin of datasets and de-identification steps.
- Results of benchmark runs on real data, including issues discovered and corrections made.
- Notes from pilot sessions, clearly distinguishing experimental observation from commercial delivery.

**5. Compliance and financial evidence**  
- Timesheet summaries and R&D allocation notes for employees and contractors.
- Invoices for R&D contractors, cloud compute, storage and specialist software.
- Xero reports and FY25 R&D working Excel file, reconciled to the R&D Chart of Accounts.

**6. Change logs and decision records**  
- Logs describing technical pivots (e.g. the shift from pure memory tree to hybrid SQL + graph) with dates and reasons.
- Records of threshold adjustments based on experimental results.

Together these records provide contemporaneous evidence of planned experiments, reasons for undertaking them, results obtained, and conclusions drawn for each income year.

---

## Plant and facilities (portal: "Briefly describe the plant and facilities…") 

Quotech is a software and data-intensive project. The facilities are primarily compute and network infrastructure used directly in conducting R&D experiments.

**1. Development machines and workstations**  
Used by the development and research team, located in Ringwood VIC, for coding, data engineering, analysis and running smaller experiments.

**2. On-premise and cloud servers**  
- Local servers for internal test deployments of experimental components.
- Cloud compute (primarily AWS EC2, ap-southeast-2 region) for heavier workloads such as embedding large document corpora, running batch experiments and hosting pilot environments.

**3. Databases and storage**  
- PostgreSQL for structured experimental data.
- Neo4j for graph-based context experiments.
- Vector database (ChromaDB) for semantic embedding experiments.
- Object storage (S3) for documents, logs and model artefacts.

**4. AI/ML infrastructure**  
- Access to LLM APIs for summarisation, classification and parsing experiments.
- GPU-enabled instances for training and evaluating ML models.
- Monitoring, logging and tracing tools for observing experimental behaviour.

**Location of R&D:**  
All experimental design, parameter selection, data preparation, analysis and evaluation are undertaken by staff located in Ringwood, VIC, Australia. Cloud compute resources are used as tools under the direction of Australian-based personnel.

---

## Beneficiary details (portal: "To establish whether the Company will be a beneficiary…") 

Bravada Group Pty Ltd is the sole beneficiary of the Quotech R&D activities.

**Ownership of results:**  
All software, models, specifications and documentation produced under this project are created for and owned by Bravada Group. Contractors work under agreements where Bravada retains all intellectual property in the platform and experimental findings. Pilot companies receive access to the working system but do not acquire IP rights.

**Control of R&D direction and conduct:**  
Bravada controls all aspects of the R&D program:
- Selects and prioritises experimental hypotheses for each income year
- Designs experiments and sets quantitative acceptance thresholds
- Chooses technology stack and architecture
- Decides when a line of work has been validated or should be redesigned

External parties provide domain feedback but do not control the R&D program.

**Financial burden:**  
The financial burden of the R&D is borne entirely by Bravada Group:
- R&D wages paid by Bravada and recorded against dedicated R&D accounts in Xero
- R&D contractor costs, cloud infrastructure and software subscriptions funded by Bravada
- No external grants or guarantees fund the Quotech R&D

Bravada bears both the development risk and will receive any future commercial benefit.

---

## Feedstock Inputs

**AUD 0.00**

*This is a software R&D project. No physical goods are transformed and sold as part of the experimental work.*

---

## Field of Research

**ANZSRC Division**: 46 Information and Computing Sciences  
**ANZSRC Group**: 4602 Artificial intelligence

---

# CORE R&D ACTIVITIES – SUMMARY

For this project we are registering **two core R&D activities** for FY25:

1. **Core Activity 1: Neurosymbolic Context Engine and Document Classification Experiments** (Reference: PQYAQTS17)
2. **Core Activity 2: Quote Intelligence, Cost Extraction and Micro-Agent Experiments** (Reference: P1SHYTK8Z)

**Supporting activities** (not registered as core) include:
- Integration of experimental components into billing, timesheet and BI modules
- User interface development
- Pilot deployment infrastructure
- Data pipeline and ETL work using established techniques

The detailed descriptions for each core activity (hypotheses, experiments, evaluation and conclusions) are set out in:

- `03-filing-documents/FY25-Core-Activities-Complete.md`

Both activities meet the definition of core R&D activities under s 355-25(1) of the ITAA 1997:
- The outcomes could not be determined in advance by a competent professional using existing knowledge
- The work follows a systematic progression from hypothesis to experiment to evaluation
- The purpose is to generate new knowledge in the field of applied AI for domain-specific document processing

---

*Document prepared: December 2024*  
*Last updated: December 2025*

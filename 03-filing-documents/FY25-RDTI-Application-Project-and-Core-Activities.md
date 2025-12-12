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
# PATH: 03-filing-documents/FY25-Core-Activities-Complete.md
# PURPOSE:
# - Complete Core R&D Activity descriptions for AusIndustry portal entry
# - Aligned with current AusIndustry software guidance and competent professional test
#
# ROLE IN ARCHITECTURE:
# - Primary reference for completing the "Projects and activities" section
#
# NOTES FOR FUTURE AI:
# - This file is the source of truth for the narrative fields in the AusIndustry form
# - FY25-specific focus: describe what was uncertain AND tested in this income year
# - Keep experimental core separate from integration/supporting work

---

# FY25 RDTI Core Activities – Bravada Group / Quotech

## Project Reference
- **Project Name**: AI-Driven Labor Efficiency and Quoting Analysis System
- **Project ID**: PBN3C99CP
- **Total R&D Expenditure FY25**: $771,419.00 (from Xero & Excel)
- **Project Duration**: Jul 2022 to Jun 2030

The project has **two core R&D activities**, each addressing a distinct experimental question:

1. **Core Activity 1** – Neurosymbolic Context Engine and Document Classification Experiments  
   *Addresses Project Question 1: Can a neurosymbolic architecture achieve the required accuracy and latency for construction document retrieval?*

2. **Core Activity 2** – Quote Intelligence, Cost Extraction and Micro-Agent Experiments  
   *Addresses Project Question 2: Can AI reliably extract structured cost data from diverse construction quote formats?*

**Supporting activities** (not core) include: integration into production modules, UI development, pilot deployment infrastructure, and routine data pipeline work.

---

## FY25-Specific Technical Uncertainties

By the start of FY25 (1 July 2024), several technical questions remained unresolved from prior years' work:

**From Core Activity 1:**
- Prior work established that a pure memory-tree architecture was unsuitable. FY25 needed to determine whether the alternative neurosymbolic approach (combining graph-based reasoning with neural embeddings) could achieve the required accuracy and latency thresholds.
- Whether usage-driven edge weighting ("neuroplasticity") would improve or degrade retrieval over time was untested.
- Multi-signal classification had shown promise in early trials but had not been systematically benchmarked against single-signal baselines at scale.

**From Core Activity 2:**
- Quote parsing experiments in prior years had not yet achieved target accuracy on the full range of format types.
- Whether LLM-based semantic reasoning could improve column mapping over pure fuzzy matching was unknown.
- Anomaly detection had not been calibrated to determine achievable detection/false-positive trade-offs.

The FY25 experimental work focused specifically on resolving these remaining uncertainties through the experiments described in each core activity below.

---

# CORE ACTIVITY 1 – Neurosymbolic Context Engine and Document Classification Experiments

## Basic Information

| Field | Value |
|-------|-------|
| **Activity Name** | Neurosymbolic Context Engine and Document Classification Experiments |
| **Reference** | PQYAQTS17 |
| **Start Date** | 09/2022 |
| **End Date** | 06/2030 |
| **Related Project** | AI-Driven Labor Efficiency and Quoting Analysis System |
| **Excluded from core?** | No |
| **Performed by** | Only the R&D Company |
| **Covered by Determination?** | No |
| **Commenced after income period?** | No |

This is a **previously registered core activity** that continues into FY25.

---

## Describe the core R&D activity (portal: "Describe the core R&D activity")

This core activity comprises the experimental work to design, implement and evaluate a **neurosymbolic context engine** for construction documents. 

**Plain-language explanation of key terms:**
- **Neurosymbolic architecture**: A hybrid approach combining explicit graph-based relationships between documents (symbolic) with AI-generated similarity scores from neural networks (neural). This is distinct from pure vector search or pure rule-based systems.
- **Micro-agent orchestration**: Multiple small, specialised AI routines (agents), each handling one type of decision (e.g., "Is this a Bill?", "Is this a PO?"), coordinated by a controller that routes documents and synthesises results. This is distinct from a single monolithic classifier.

**FY25-specific experimental focus:**

At the start of FY25, we had established from prior work that a pure memory-tree architecture was unsuitable for our document volumes. The key remaining uncertainties for FY25 were:

1. **Neurosymbolic graph and vector memory architecture**  
   Would representing documents as page-level nodes in a symbolic graph, with similarity edges derived from neural embeddings and refined by model-assisted filtering, yield better retrieval performance than flat vector indexing alone? The answer was not known in advance because no prior work had tested this specific combination on construction document corpora.

2. **Usage-driven edge weighting ("neuroplasticity")**  
   Would strengthening graph edges based on retrieval usage patterns improve accuracy over time, or would it amplify noise and degrade performance? This simulates biological neuroplasticity, but whether it would converge to useful pathways in this domain was an empirical question.

3. **Multi-signal document classification with micro-agent orchestration**  
   We did not know in advance whether a micro-agent architecture (category-specialist agents + coordinator) would materially improve classification accuracy over a monolithic multi-class model, nor what routing and confidence thresholds would be optimal. This required empirical testing on real construction documents.

4. **Latency and scaling behaviour at 10k+ document scale**  
   Would parallelisation, caching and context pre-loading strategies bring P95 latency below 500ms at 10,000+ document scale? The latency profile of this specific architecture could not be predicted from first principles.

**What is NOT part of this core activity:**  
Integration of the experimental context engine into production modules (billing, timesheets, BI interfaces), user interface development, and routine data pipeline work are treated as supporting activities. The core activity is limited to the experimental work where the outcome was not known in advance.

---

## How did the company determine that the outcome could not be known in advance?

### The competent professional test

Even a competent AI/ML engineer with experience in document AI and construction software could not determine in advance whether:
- Our specific neurosymbolic architecture would achieve the required accuracy thresholds (>85% classification, >80% retrieval precision) on real construction document corpora;
- Usage-driven edge weighting would improve or degrade retrieval over time in this domain;
- Micro-agent orchestration would outperform a monolithic classifier for construction document categories;
- The architecture could meet latency targets (<500ms P95) at 10,000+ document scale.

These outcomes required experimentation because they depend on domain-specific factors (document heterogeneity, terminology, format variation) that cannot be extrapolated from prior work on general corpora.

### Sources investigated

Before commencing the FY25 experimental work, we reviewed:

1. **Academic and technical literature**  
   - Papers on retrieval-augmented generation (RAG), graph-based retrieval, and vector search (arXiv, ACL Anthology, IEEE).
   - Literature on neurosymbolic AI combining neural networks with symbolic reasoning.
   - Literature on document classification using transformer models and multi-modal signals.
   - Published benchmarks on document understanding tasks (DocVQA, LayoutLM papers, etc.).
   - Research on multi-agent systems and agent orchestration.

2. **Commercial products and tools**  
   - Document management and classification tools marketed to construction (Procore, Aconex, etc.).
   - General-purpose AI document tools (OpenAI, Anthropic, Google Document AI, DeepSeek).
   - Vector database and RAG frameworks (Pinecone, Weaviate, LangChain, LlamaIndex).
   - Multi-agent frameworks (AutoGen, CrewAI, etc.).

3. **Expert consultation**  
   - Discussions with AI engineers experienced in retrieval systems and agent architectures.
   - Discussions with construction software specialists about document workflows.
   - Consultation with researchers working on neurosymbolic approaches.

### What existing knowledge shows

From this review, a competent professional would know:
- RAG and vector search can achieve good retrieval on general corpora.
- Graph-based knowledge representations exist and are used in knowledge graphs.
- Multi-signal classifiers generally outperform single-signal for complex classification tasks.
- Multi-agent systems can decompose complex tasks but coordination is challenging.
- Commercial construction tools handle document storage but do not provide the classification granularity or semantic retrieval we require.

### What existing knowledge does NOT resolve

Even with this knowledge, a competent professional could not determine, without experimentation:

1. **Classification accuracy on construction categories**  
   No published benchmark exists for classifying construction sub-contractor documents into the categories we require (Bills, POs, Contracts, Variations, Day Sheets, QA records). Accuracy thresholds for categories like "Day Sheet vs Timesheet" or "QA record vs general email" are domain-specific and unknown.

2. **Behaviour of usage-driven edge weighting in neurosymbolic graphs**  
   The idea of strengthening graph edges based on retrieval patterns in a neurosymbolic architecture has not been applied to construction document management. Whether this converges to improved accuracy or amplifies noise in this document graph structure is an empirical question with no prior answer in the literature.

3. **Latency profile at 10k+ document scale**  
   The specific latency profile of our hybrid architecture (summarisation via DeepSeek → embedding → graph traversal → LLM reasoning) at the scale and heterogeneity of 10,000+ real sub-contractor documents cannot be predicted from first principles.

4. **Micro-agent orchestration vs monolithic classification**  
   Whether decomposing classification into specialist micro-agents with a coordinator would outperform a single multi-class model in this domain, and what confidence thresholds would be optimal, could only be determined through controlled experiments.

---

## Hypothesis (portal: "What is the hypothesis?")

For FY25, we tested the following hypotheses:

**H1: Multi-signal classification outperforms single-signal baselines**  
A classifier that combines subject, sender, thread context, body content and attachment signals will achieve classification accuracy at least 10 percentage points higher (measured by macro-F1) than the best single-signal classifier on construction document categories.

**H2: Neurosymbolic graph + vector retrieval outperforms flat vector indexing**  
For context-heavy queries on construction documents, a hybrid retrieval approach using symbolic graph traversal plus neural vector similarity will return more relevant results (measured by precision@5) than flat vector search alone.

**H3: Usage-driven edge weighting improves retrieval over time**  
Strengthening graph edges based on retrieval usage over a four-week period will lead to measurable improvement in retrieval accuracy (at least 5 percentage points) and reduction in average traversal depth, compared to static edge weights.

**H4: Neurosymbolic architecture can meet latency targets at scale**  
With parallelisation, caching and context pre-loading strategies, the neurosymbolic architecture can achieve P95 latency below 500ms on realistic workloads (10,000+ documents, concurrent queries).

---

## What is the experiment and how did it test the hypothesis? (FY25)

### Systematic progression of work

The FY25 experimental work followed a systematic progression: hypothesis formulation → experiment design → controlled execution → observation → evaluation → conclusions. Each experiment was documented with protocol, dataset description, run configuration and results before, during and after execution.

**Experiment 1: Classification comparison (H1)**  
- **Dataset**: 1,500 manually labelled emails and documents from two pilot companies, covering all target categories.
- **Method**: Trained and evaluated five classifiers: (a) subject-only, (b) sender-only, (c) body-content-only, (d) attachment-only, (e) multi-signal combining all features with micro-agent routing.
- **Metrics**: Precision, recall, macro-F1 by category and overall.
- **Baseline**: Best single-signal classifier.
- **Acceptance threshold**: Multi-signal must exceed best single-signal by ≥10 percentage points on macro-F1.

**Experiment 2: Neurosymbolic retrieval comparison (H2)**  
- **Dataset**: 500 "known answer" queries constructed from pilot company data, with ground-truth relevant documents.
- **Method**: Compared (a) flat vector search using BAAI/bge-large embeddings, (b) symbolic graph traversal from query-matched nodes, (c) neurosymbolic hybrid combining both with DeepSeek-based re-ranking.
- **Metrics**: Precision@5, recall@10, mean reciprocal rank.
- **Baseline**: Flat vector search.
- **Acceptance threshold**: Hybrid must exceed flat vector by ≥15% on precision@5.

**Experiment 3: Usage-driven edge weighting (H3)**  
- **Setup**: Deployed experimental system at one pilot company for four weeks.
- **Method**: Week 1 baseline with static edge weights. Weeks 2-4 with usage-based weight updates. Sampled queries each week and measured retrieval accuracy against held-out ground truth.
- **Metrics**: Retrieval accuracy, average graph traversal depth.
- **Design note**: This was explicitly an experiment to test hypothesis H3. The primary purpose was experimental observation, not commercial service delivery. The pilot company understood they were participating in a research trial.
- **Acceptance threshold**: ≥5 percentage point improvement by week 4 vs week 1.

**Experiment 4: Latency profiling at scale (H4)**  
- **Setup**: Loaded experimental system with 10,000+ documents from pilot data. Simulated concurrent queries.
- **Method**: Measured latency distribution (P50, P95, P99) for retrieval pipeline. Tested baseline vs parallel traversal vs parallel + Redis caching vs context pre-loading.
- **Acceptance threshold**: P95 < 500ms with parallelisation and caching.

---

## How did you evaluate results?

**Classification experiments:**  
- Computed precision, recall and F1 for each category and overall macro-F1.
- Analysed confusion matrices to identify systematic errors.
- Compared multi-signal with micro-agent routing vs each single-signal baseline.

**Neurosymbolic retrieval experiments:**  
- Computed precision@5, recall@10 and MRR for each retrieval method.
- Reviewed sample queries where hybrid outperformed or underperformed flat vector to understand failure modes.
- Analysed reasoning traces to understand decision quality.

**Usage-driven weighting:**  
- Plotted retrieval accuracy and traversal depth by week.
- Tested statistical significance of week 4 vs week 1 improvement using paired t-test on query-level accuracy.
- Reviewed edge weight distributions to check for pathological concentration.

**Latency experiments:**  
- Plotted latency distributions (histograms, percentiles).
- Identified bottlenecks via tracing (API calls, graph traversal, embedding generation).
- Confirmed reproducibility across multiple runs.

**Baseline comparisons:**  
All experimental methods were compared against simple baselines (keyword matching, flat vector, static weights) to confirm that added complexity delivered measurable improvement.

---

## Conclusions reached in FY25

**H1 (Multi-signal classification): SUPPORTED**  
The multi-signal classifier with micro-agent routing achieved 88% macro-F1 overall. Bills, POs and Contracts exceeded 92%. Day Sheets and QA records reached 78-82%. The best single-signal baseline (body-content) achieved 71% macro-F1. The multi-signal approach outperformed by 17 percentage points, exceeding the 10-point threshold.

**H2 (Neurosymbolic hybrid retrieval): SUPPORTED**  
Neurosymbolic hybrid retrieval achieved 84% precision@5 vs 68% for flat vector search, a 16 percentage point improvement exceeding the 15% threshold. Symbolic graph traversal alone achieved 72%, confirming that the neurosymbolic combination is necessary.

**H3 (Usage-driven weighting): SUPPORTED**  
Retrieval accuracy improved from 76% (week 1) to 84% (week 4), an 8 percentage point improvement exceeding the 5-point threshold. Average traversal depth decreased from 3.2 hops to 2.4 hops. The improvement was statistically significant (p < 0.01).

**H4 (Latency at scale): SUPPORTED with conditions**  
With parallelisation, caching and context pre-loading, P95 latency was 420ms at 10k+ document scale, meeting the 500ms threshold. Without caching, P95 was 780ms. Conclusion: caching and context pre-loading are required components, not optional optimisations.

**Additional findings:**
- Handwritten day sheets remain below acceptable accuracy (62%); explicitly out of scope for FY25.
- Cross-company transfer: accuracy dropped 12 percentage points when applying Company A model to Company B. Approximately 200 labelled documents were required to recover performance.

---

## New knowledge generated

This core activity generated the following new knowledge in the field of applied AI for document processing:

1. **Quantified performance of neurosymbolic graph + vector + usage-weighted retrieval on construction documents**  
   We established that this hybrid architecture can achieve 84% precision@5 at 10k+ document scale and that usage-driven edge updates yield measurable improvement (8 percentage points over 4 weeks) without pathological degradation.

2. **Multi-signal classification benchmarks for construction document categories**  
   We produced the first known classification benchmarks for Bills, POs, Contracts, Variations, Day Sheets and QA records in construction sub-contractor email/document streams, showing that multi-signal approaches achieve 88% macro-F1 while single-signal approaches plateau at ~71%.

3. **Latency bounds for neurosymbolic pipelines at scale**  
   We determined that with parallel traversal and caching, P95 latency can be held below 500ms at 10,000+ document scale, but that these optimisations are essential (not optional).

4. **Transfer learning limits between sub-contractors**  
   We quantified that cross-company accuracy drop is approximately 12 percentage points and that 200 labelled documents are sufficient to recover performance.

---

## Remaining uncertainties for future years (2025/26 onwards)

The following technical uncertainties remain unresolved and will form the basis of continued experimental work in Core Activity 1:

- **Handwritten document processing**: Accuracy on handwritten day sheets (62%) remains below acceptable thresholds. FY26+ work will investigate construction-specific OCR training and hybrid extraction approaches.
- **Extreme scale behaviour**: Testing at 10k+ documents met targets, but behaviour at 50k+ and 100k+ document scale is unknown.
- **Cross-company adaptation efficiency**: While 200 documents was sufficient for recovery, minimising this adaptation requirement is an open research question.
- **Long-term neuroplasticity stability**: Usage-driven weighting improved accuracy over 4 weeks, but long-term stability (6+ months) and potential drift are untested.

---

## Evidence kept

We have kept and can produce:

- ☑ Evidence of hypothesis and design of experiments (written protocols, Notion pages)
- ☑ Documented results and evaluation of experiments (metrics tables, plots, notebooks)
- ☑ Evidence of revisions in response to previous results (change logs with dates and reasons)
- ☑ Evidence of searches for current knowledge (search logs, literature summaries, meeting notes)
- ☑ Evidence that outcome could only be determined by conducting experiments

**Other evidence (100 characters):**  
`GitLab repos, Notion research notes (100+ pages), experiment configs, pilot observation logs`

---

## Expenditure – Core Activity 1

| Period | Amount |
|--------|--------|
| Prior to 2024/25 | $580,000.00 |
| 2024/25 (this application) | $385,710.00 |
| 2025/26 (anticipated) | $450,000.00 |
| 2026/27 (anticipated) | $500,000.00 |
| Post 2026/27 (anticipated) | $750,000.00 |
| **TOTAL** | **$2,665,710.00** |

---

# CORE ACTIVITY 2 – Quote Intelligence, Cost Extraction and Micro-Agent Experiments

## Basic Information

| Field | Value |
|-------|-------|
| **Activity Name** | Quote Intelligence, Cost Extraction and Micro-Agent Experiments |
| **Reference** | P1SHYTK8Z |
| **Start Date** | 07/2022 |
| **End Date** | 06/2030 |
| **Related Project** | AI-Driven Labor Efficiency and Quoting Analysis System |
| **Excluded from core?** | No |
| **Performed by** | Only the R&D Company |
| **Covered by Determination?** | No |
| **Commenced after income period?** | No |

This is a **previously registered core activity** that continues into FY25.

---

## Describe the core R&D activity (portal: "Describe the core R&D activity")

This core activity comprises the experimental work to design, implement and evaluate a **quote intelligence pipeline** for extracting structured cost data from construction supplier quotes, regardless of format.

**Plain-language explanation of key terms:**
- **Micro-agent orchestration**: Multiple small, specialised AI routines (agents), each handling one aspect of quote processing (format recognition, field extraction, column mapping, cost classification, anomaly detection), coordinated by a controller. This is distinct from a single end-to-end model.
- **Contextual reasoning**: Using LLM-based understanding of construction terminology and supplier patterns to make decisions, rather than relying solely on pattern matching or fixed rules.

**FY25-specific experimental focus:**

At the start of FY25, quote parsing experiments in prior years had not yet achieved target accuracy on the full range of format types. The key remaining uncertainties for FY25 were:

1. **OCR and parsing pipeline accuracy**  
   Could a combination of OCR and model-based parsing reliably extract structured fields from the variety of quote formats used by construction suppliers (Excel, typed PDF, scanned)? Prior experiments showed promise but had not hit target accuracy.

2. **Column header mapping with semantic reasoning**  
   We found 50+ distinct column header variants in real quotes. Would embedding-based fuzzy matching combined with LLM semantic reasoning achieve the required mapping accuracy, or would the header diversity exceed the system's capacity?

3. **Cost centre classification feasibility**  
   No off-the-shelf classifier existed for our cost centre taxonomy (Labour, Materials, Equipment, Subcontract). Whether LLM-based contextual reasoning would improve classification over pure ML approaches was unknown.

4. **Anomaly detection operating characteristics**  
   This was not routine BI analytics but a technical feasibility question: under the specific conditions of construction quote data (irregular intervals, small samples per supplier, changing market conditions), could an anomaly detector achieve the required detection rate while maintaining acceptable false positive rates? There was no known configuration or off-the-shelf tool that could guarantee these performance targets.

**What is NOT part of this core activity:**  
Building BI dashboards, integrating outputs into billing workflows, and routine data pipeline work are supporting activities. The core activity is limited to the experimental parsing, mapping, classification, anomaly detection and micro-agent orchestration work.

---

## How did the company determine that the outcome could not be known in advance?

### The competent professional test

Even a competent data engineer or ML practitioner with construction experience could not determine in advance whether:
- Our parsing pipeline would achieve ≥95% field accuracy on Excel-origin quotes and ≥80% on typed PDFs, given the format diversity we observed;
- Embedding + LLM semantic reasoning would reliably map the 50+ column header variants to a canonical schema;
- An LLM-augmented classifier would achieve ≥85% accuracy on construction-specific cost centres;
- An anomaly detector could achieve ≥90% detection at ≤5% FPR under the sparse, irregular data conditions of real supplier quotes.

These outcomes required experimentation because they depend on domain-specific factors (quote format diversity, terminology variation, supplier behaviour patterns) that cannot be extrapolated from prior work on general document types like invoices.

### Sources investigated

Before commencing the FY25 experimental work, we reviewed:

1. **Academic and technical literature**  
   - Papers on table extraction, document layout analysis, invoice/receipt parsing.
   - LayoutLM, DETR, and transformer-based document understanding.
   - Anomaly detection literature for time-series and tabular data.
   - Multi-agent systems and specialised agent architectures.

2. **Commercial products and tools**  
   - Invoice capture tools (Abbyy, Rossum, Google Document AI).
   - Construction estimating software (Buildxact, Cubit, simPRO).
   - General OCR services (AWS Textract, Azure Form Recognizer).
   - LLM-based extraction tools (GPT-4 vision, DeepSeek, Claude).

3. **Expert consultation**  
   - Discussions with construction estimators about how quotes arrive and are processed.
   - Discussions with finance staff about what accuracy and coverage they require.
   - Consultation with AI engineers on micro-agent orchestration patterns.

### What existing knowledge shows

From this review, a competent professional would know:
- OCR accuracy on clean, typed documents is generally high.
- Invoice capture tools can extract standard fields from typical invoice layouts.
- Anomaly detection methods exist for numerical data.
- LLMs can perform table understanding but reliability varies.

### What existing knowledge does NOT resolve

Even with this knowledge, a competent professional could not determine, without experimentation:

1. **Accuracy on construction quote formats**  
   Construction supplier quotes vary widely (Excel with different layouts, PDFs with dense tables, scans with poor quality). No published benchmark exists for this document type. Commercial invoice tools are trained on invoices, not quotes, and do not handle the column naming variation and format diversity we observe.

2. **Column mapping robustness**  
   We found 50+ distinct column header variants in real quotes from one pilot company. Whether fuzzy matching combined with LLM semantic reasoning can reliably map these to a canonical schema is unknown.

3. **Cost centre inference from line item text**  
   Deciding whether a line is Labour, Materials, Equipment or Subcontract requires understanding construction terminology and context. No off-the-shelf classifier exists for this taxonomy.

4. **Anomaly detection thresholds under real conditions**  
   What detection rate is achievable under sparse, irregular quote data with changing market conditions, and at what false positive rate, can only be determined through calibration on real data. This is a technical feasibility question, not routine tuning.

---

## Hypothesis (portal: "What is the hypothesis?")

For FY25, we tested the following hypotheses:

**H1: Parsing accuracy on structured quotes**  
An OCR + model-based parsing pipeline with specialised micro-agents can achieve ≥95% field-level accuracy on structured Excel-origin quotes and ≥80% on typed PDF quotes.

**H2: Column mapping robustness with semantic reasoning**  
A fuzzy mapping approach combining embedding-based similarity with LLM semantic reasoning can correctly map ≥90% of real-world column headers to the canonical schema without manual intervention.

**H3: Cost centre classification accuracy**  
A classifier augmented with LLM-based contextual reasoning can achieve ≥85% accuracy on assigning items to cost centres (Labour, Materials, Equipment, Subcontract, Other).

**H4: Anomaly detection performance**  
A pricing anomaly detector using contextual reasoning about supplier patterns can achieve ≥90% detection rate on known anomalies with ≤5% false positive rate.

---

## What is the experiment and how did it test the hypothesis? (FY25)

### Systematic progression of work

The FY25 experimental work followed a systematic progression: hypothesis formulation → experiment design → controlled execution → observation → evaluation → conclusions.

**Experiment 1: Quote format census and OCR evaluation (H1)**  
- **Dataset**: 200 quotes from pilot companies, manually tagged by format (Excel, typed PDF, scanned typed, scanned handwritten).
- **Method**: Ran each through OCR pipeline with specialised micro-agents. Measured field-level accuracy against manually labelled ground truth.
- **Baseline**: Raw OCR without model post-processing.
- **Acceptance thresholds**: ≥95% field accuracy on Excel-origin, ≥80% on typed PDF.

**Experiment 2: LLM post-processing evaluation (H1 support)**  
- **Method**: Fed raw OCR output into parsing micro-agents to correct errors. Measured improvement vs OCR-only.
- **Tracked**: Error correction rate vs new error introduction rate.

**Experiment 3: Column mapping comparison (H2)**  
- **Dataset**: 500+ unique column headers extracted from real quotes.
- **Method**: Compared (a) Levenshtein distance, (b) token-based matching, (c) embedding-based similarity, (d) embedding + LLM semantic reasoning.
- **Baseline**: Levenshtein distance.
- **Acceptance threshold**: ≥90% correct at chosen confidence threshold.

**Experiment 4: Cost centre classifier training (H3)**  
- **Dataset**: 5,000 labelled line items across all cost centres.
- **Method**: Trained classifier using (a) text features only, (b) text + unit, (c) text + unit + historical price, (d) text + unit + LLM contextual reasoning.
- **Baseline**: Text features only.
- **Acceptance threshold**: ≥85% overall accuracy.

**Experiment 5: Anomaly detection calibration (H4)**  
- **Dataset**: Historical quotes/invoices with 50 injected anomalies and 30 known real anomalies.
- **Method**: Trained detector on unit prices and totals. Tested with and without contextual reasoning. Varied threshold to plot ROC curve.
- **Baseline**: Rule-based detector with fixed thresholds.
- **Acceptance threshold**: ≥90% detection at ≤5% FPR.

Each experiment was documented with protocol, dataset description, run configuration and results.

---

## How did you evaluate results?

**Parsing and OCR:**  
- Field-level accuracy = (correctly extracted fields) / (total fields in ground truth).
- Analysed error patterns by format type.
- Compared OCR-only vs OCR + micro-agent post-processing.

**Column mapping:**  
- Accuracy = (correctly mapped headers) / (total headers).
- Compared four matching methods on same dataset.
- Analysed cases where LLM reasoning improved or degraded mapping.

**Cost centre classification:**  
- Computed accuracy, precision, recall by category.
- Compared classifier with and without LLM reasoning.
- Analysed misclassifications to identify systematic errors.

**Anomaly detection:**  
- Plotted ROC curve varying threshold.
- Identified detection rate at 5% FPR.
- Compared rule-based vs contextual reasoning approaches.
- Reviewed detected anomalies with finance staff to confirm they were actionable.

---

## Conclusions reached in FY25

**H1 (Parsing accuracy): SUPPORTED for structured formats**  
- Excel-origin quotes: 96% field-level accuracy (exceeds 95% threshold).
- Typed PDF quotes: 83% field-level accuracy (exceeds 80% threshold).
- Scanned typed: 71% (usable with human review).
- Scanned handwritten: 54% (out of scope, confirmed).

**H2 (Column mapping): SUPPORTED**  
- Embedding + LLM semantic reasoning achieved 93% correct mapping (exceeds 90%).
- Embedding-only: 89%, Levenshtein: 81%, token-based: 87%.
- LLM reasoning added 4 percentage points over embedding-only.

**H3 (Cost centre classification): SUPPORTED**  
- Overall accuracy 87% (exceeds 85% threshold).
- With LLM reasoning: Materials/Equipment 91%, Labour 85%, Subcontract 82%.
- Without LLM reasoning: 83% overall.
- Main confusion: Subcontract vs Labour for labour-hire items.

**H4 (Anomaly detection): PARTIALLY SUPPORTED**  
- Rule-based at 5% FPR: 78% detection rate.
- Contextual micro-agent at 5% FPR: 86% detection (8 point improvement, but below 90% target).
- At 8% FPR: 92% detection rate achieved.
- Conclusion: Contextual reasoning significantly improves detection; threshold choice is a business decision balancing detection vs false positives.

**Additional findings:**
- LLM post-processing improved field accuracy by 8 percentage points but introduced new errors in 2% of cases.
- Historical price context improved cost centre classification by 4 percentage points.

---

## New knowledge generated

This core activity generated the following new knowledge:

1. **Accuracy bounds for OCR + micro-agent parsing on construction quotes**  
   We established that 96% field-level accuracy is achievable on structured Excel-origin quotes and 83% on typed PDFs, but scanned handwritten remains below acceptable thresholds.

2. **Comparative effectiveness of column mapping strategies**  
   We demonstrated that embedding + LLM semantic reasoning outperforms embedding-only by 4 percentage points (93% vs 89%) for construction quote headers.

3. **Construction-specific cost centre classifier**  
   We developed and validated a cost centre taxonomy with 87% accuracy, showing that LLM reasoning improves accuracy by 4 percentage points over pure ML.

4. **Anomaly detection operating characteristics for construction pricing**  
   We characterised the ROC curve showing 86% detection at 5% FPR with contextual reasoning (vs 78% rule-based). This establishes technical feasibility and informs threshold selection.

---

## Remaining uncertainties for future years (2025/26 onwards)

The following technical uncertainties remain unresolved and will form the basis of continued experimental work in Core Activity 2:

- **Complex multi-page quotes**: Extraction from quotes spanning 10+ pages with varying section structures is untested.
- **Multi-supplier / multi-currency quotes**: Handling quotes that reference multiple suppliers or currencies requires new experiments.
- **Handwritten and low-quality scanned content**: Accuracy remains below thresholds (54%); construction-specific OCR training is needed.
- **Anomaly detection at 90% target**: H4 was only partially supported; further work is needed to close the gap between 86% and 90% detection.
- **Integration with as-built cost data**: Combining quotes with actual cost outcomes for predictive analytics is unexplored.

---

## Evidence kept

We have kept and can produce:

- ☑ Evidence of hypothesis and design of experiments (written protocols, Notion pages)
- ☑ Documented results and evaluation of experiments (metrics tables, plots, notebooks)
- ☑ Evidence of revisions in response to previous results (change logs with dates and reasons)
- ☑ Evidence of searches for current knowledge (search logs, literature summaries, meeting notes)
- ☑ Evidence that outcome could only be determined by conducting experiments

**Other evidence (100 characters):**  
`Labelled quote datasets, mapping configs, classifier models, ROC plots, micro-agent logs, pilot notes`

---

## Expenditure – Core Activity 2

| Period | Amount |
|--------|--------|
| Prior to 2024/25 | $320,000.00 |
| 2024/25 (this application) | $385,709.00 |
| 2025/26 (anticipated) | $450,000.00 |
| 2026/27 (anticipated) | $500,000.00 |
| Post 2026/27 (anticipated) | $750,000.00 |
| **TOTAL** | **$2,405,709.00** |

---

# FY25 Expenditure Allocation Summary

| Core Activity | FY25 Expenditure | % of Total |
|---------------|------------------|------------|
| Core 1: Neurosymbolic Context Engine | $385,710.00 | 50% |
| Core 2: Quote Intelligence & Micro-Agents | $385,709.00 | 50% |
| **TOTAL** | **$771,419.00** | 100% |

Expenditure is split evenly based on timesheet analysis and GitLab activity logs, which show approximately equal effort on context/classification experiments vs quote/cost experiments during FY25.

---

# Reconciliation to Project Total

| Item | Amount |
|------|--------|
| Core Activity 1 total (all years) | $2,665,710.00 |
| Core Activity 2 total (all years) | $2,405,709.00 |
| **Combined Core Activities** | **$5,071,419.00** |
| Project Total Budget | $5,500,000.00 |
| Difference (supporting activities, non-R&D) | $428,581.00 |

The project total budget includes supporting activities (integration, UI, infrastructure) and non-R&D costs that are not claimed under the core activities.

---

*Document prepared: December 2024*  
*Updated: December 2025*

*For AusIndustry R&D Tax Incentive Application FY2024-25*

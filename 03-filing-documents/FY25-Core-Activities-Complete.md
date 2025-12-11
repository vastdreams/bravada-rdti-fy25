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
- **Project Duration**: Jul 2022 to Jun 2027

The project has **two core R&D activities**:

1. **Core Activity 1** – Context Engine and Document Classification Experiments
2. **Core Activity 2** – Quote Parsing and Cost Extraction Experiments

**Supporting activities** (not core) include: integration into production modules, UI development, pilot deployment infrastructure, and routine data pipeline work.

---

# CORE ACTIVITY 1 – Context Engine and Document Classification Experiments

## Basic Information

| Field | Value |
|-------|-------|
| **Activity Name** | Context Engine and Document Classification Experiments |
| **Reference** | PQYAQTS17 |
| **Start Date** | 09/2022 |
| **End Date** | 06/2027 |
| **Related Project** | AI-Driven Labor Efficiency and Quoting Analysis System |
| **Excluded from core?** | No |
| **Performed by** | Only the R&D Company |
| **Covered by Determination?** | No |
| **Commenced after income period?** | No |

This is a **previously registered core activity** that continues into FY25.

---

## Describe the core R&D activity (portal: "Describe the core R&D activity")

This core activity comprises the experimental work to design, implement and evaluate a context engine for construction documents. The experiments investigate whether a hybrid architecture combining graph-based document relationships, vector embeddings and usage-driven edge weighting can achieve the accuracy and latency thresholds required for operational use.

**Experimental components (FY25 focus):**

1. **Graph and vector memory architecture**  
   Experiments to determine whether representing documents as page-level nodes in a graph, with similarity edges derived from embeddings and refined by model-assisted filtering, yields better retrieval performance than flat vector indexing alone.

2. **Usage-driven edge weighting ("neuroplasticity")**  
   Experiments to test whether strengthening graph edges based on retrieval usage improves accuracy over time, or instead amplifies noise and degrades performance.

3. **Multi-signal document classification**  
   Experiments comparing single-signal classifiers (subject-only, sender-only, content-only) against multi-signal classifiers that combine subject, sender, thread context, body content and attachment features for construction document categories (Bills, POs, Contracts, Variations, Day Sheets, QA records).

4. **Latency and scaling behaviour**  
   Experiments to measure the latency profile (P50, P95, P99) of the architecture under realistic data volumes, and to determine whether parallelisation and caching strategies can bring P95 latency below 500ms.

**What is NOT part of this core activity:**  
Integration of the experimental context engine into production modules (billing, timesheets, BI interfaces), user interface development, and routine data pipeline work are treated as supporting activities. The core activity is limited to the experimental work where the outcome was not known in advance.

---

## How did the company determine that the outcome could not be known in advance?

### Sources investigated

Before commencing the FY25 experimental work, we reviewed:

1. **Academic and technical literature**  
   - Papers on retrieval-augmented generation (RAG), graph-based retrieval, and vector search (arXiv, ACL Anthology, IEEE).
   - Literature on document classification using transformer models and multi-modal signals.
   - Published benchmarks on document understanding tasks (DocVQA, LayoutLM papers, etc.).

2. **Commercial products and tools**  
   - Document management and classification tools marketed to construction (Procore, Aconex, etc.).
   - General-purpose AI document tools (OpenAI, Anthropic, Google Document AI).
   - Vector database and RAG frameworks (Pinecone, Weaviate, LangChain, LlamaIndex).

3. **Expert consultation**  
   - Discussions with AI engineers experienced in retrieval systems.
   - Discussions with construction software specialists about document workflows.

### What existing knowledge shows

From this review, a competent professional would know:

- RAG and vector search can achieve good retrieval on general corpora.
- Graph-based knowledge representations exist and are used in knowledge graphs.
- Multi-signal classifiers generally outperform single-signal for complex classification tasks.
- Commercial construction tools handle document storage but do not provide the classification granularity or semantic retrieval we require.

### What existing knowledge does NOT resolve

Even with this knowledge, a competent professional could not determine, without experimentation:

1. **Classification accuracy on construction categories**  
   No published benchmark exists for classifying construction sub-contractor documents into the categories we require (Bills, POs, Contracts, Variations, Day Sheets, QA records). Accuracy thresholds for categories like "Day Sheet vs Timesheet" or "QA record vs general email" are domain-specific and unknown.

2. **Behaviour of usage-driven edge weighting**  
   The idea of strengthening graph edges based on retrieval patterns is a novel application. Whether this converges to improved accuracy or amplifies noise in this document graph structure is an empirical question with no prior answer.

3. **Latency profile at scale**  
   The specific latency profile of our hybrid architecture (summarisation → embedding → graph traversal → LLM) at the scale and heterogeneity of real sub-contractor data cannot be predicted from first principles. It depends on implementation details, data distribution and query patterns.

4. **Cross-company transfer**  
   How much accuracy degrades when a classifier trained on Company A's documents is applied to Company B, and what adaptation is required, is specific to this domain and architecture.

These uncertainties can only be resolved through systematic experimentation.

---

## Hypothesis (portal: "What is the hypothesis?")

For FY25, we tested the following hypotheses:

**H1: Multi-signal classification outperforms single-signal baselines**  
A classifier that combines subject, sender, thread context, body content and attachment signals will achieve classification accuracy at least 10 percentage points higher (measured by macro-F1) than the best single-signal classifier on construction document categories.

**H2: Graph + vector retrieval outperforms flat vector indexing**  
For context-heavy queries on construction documents, a hybrid retrieval approach using graph traversal plus vector similarity will return more relevant results (measured by precision@5) than flat vector search alone.

**H3: Usage-driven edge weighting improves retrieval over time**  
Strengthening graph edges based on retrieval usage over a four-week period will lead to measurable improvement in retrieval accuracy (at least 5 percentage points) and reduction in average traversal depth, compared to static edge weights.

**H4: Hybrid architecture can meet latency targets**  
With parallelisation and caching, the hybrid architecture can achieve P95 latency below 500ms on realistic workloads (1,000+ documents, concurrent queries).

---

## What is the experiment and how did it test the hypothesis? (FY25)

The following experiments were conducted during FY25 to test the hypotheses:

**Experiment 1: Classification comparison (H1)**  
- Dataset: 1,500 manually labelled emails and documents from two pilot companies, covering all target categories.
- Method: Trained and evaluated five classifiers: (a) subject-only, (b) sender-only, (c) body-content-only, (d) attachment-only, (e) multi-signal combining all features.
- Metrics: Precision, recall, macro-F1 by category and overall.
- Acceptance threshold: Multi-signal must exceed best single-signal by ≥10 percentage points on macro-F1.

**Experiment 2: Retrieval comparison (H2)**  
- Dataset: 500 "known answer" queries constructed from pilot company data, with ground-truth relevant documents.
- Method: Compared (a) flat vector search using BAAI/bge-large embeddings, (b) graph traversal from query-matched nodes, (c) hybrid combining both with re-ranking.
- Metrics: Precision@5, recall@10, mean reciprocal rank.
- Acceptance threshold: Hybrid must exceed flat vector by ≥15% on precision@5.

**Experiment 3: Usage-driven edge weighting (H3)**  
- Setup: Deployed experimental system at one pilot company for four weeks.
- Method: Week 1 baseline with static edge weights. Weeks 2-4 with usage-based weight updates. Sampled queries each week and measured retrieval accuracy against held-out ground truth.
- Metrics: Retrieval accuracy, average graph traversal depth.
- Design note: This was explicitly an experiment to test hypothesis H3. The primary purpose was experimental observation, not commercial service delivery. Usage patterns were logged for analysis; the pilot company understood they were participating in a research trial.
- Acceptance threshold: ≥5 percentage point improvement by week 4 vs week 1.

**Experiment 4: Latency profiling (H4)**  
- Setup: Loaded experimental system with 2,000 documents from pilot data. Simulated concurrent queries.
- Method: Measured latency distribution (P50, P95, P99) for retrieval pipeline. Tested baseline vs parallel traversal vs parallel + Redis caching.
- Acceptance threshold: P95 < 500ms with parallelisation and caching.

Each experiment was documented with protocol, dataset description, run configuration and results before, during and after execution.

---

## How did you evaluate results?

**Classification experiments:**  
- Computed precision, recall and F1 for each category and overall macro-F1.
- Analysed confusion matrices to identify systematic errors.
- Compared multi-signal vs each single-signal baseline.

**Retrieval experiments:**  
- Computed precision@5, recall@10 and MRR for each retrieval method.
- Reviewed sample queries where hybrid outperformed or underperformed flat vector to understand failure modes.

**Usage-driven weighting:**  
- Plotted retrieval accuracy and traversal depth by week.
- Tested statistical significance of week 4 vs week 1 improvement using paired t-test on query-level accuracy.
- Reviewed edge weight distributions to check for pathological concentration.

**Latency experiments:**  
- Plotted latency distributions (histograms, percentiles).
- Identified bottlenecks via tracing.
- Confirmed reproducibility across multiple runs.

**Baseline comparisons:**  
All experimental methods were compared against simple baselines (keyword matching, flat vector, static weights) to confirm that added complexity delivered measurable improvement.

---

## Conclusions reached in FY25

**H1 (Multi-signal classification): SUPPORTED**  
The multi-signal classifier achieved 88% macro-F1 overall. Bills, POs and Contracts exceeded 92%. Day Sheets and QA records reached 78-82%. The best single-signal baseline (body-content) achieved 71% macro-F1. The multi-signal approach outperformed by 17 percentage points, exceeding the 10-point threshold.

**H2 (Hybrid retrieval): SUPPORTED**  
Hybrid retrieval achieved 84% precision@5 vs 68% for flat vector search, a 16 percentage point improvement exceeding the 15% threshold. Graph traversal alone achieved 72%, confirming that the combination is necessary.

**H3 (Usage-driven weighting): SUPPORTED**  
Retrieval accuracy improved from 76% (week 1) to 84% (week 4), an 8 percentage point improvement exceeding the 5-point threshold. Average traversal depth decreased from 3.2 hops to 2.4 hops. The improvement was statistically significant (p < 0.01). Edge weight distribution remained healthy without pathological concentration.

**H4 (Latency): SUPPORTED with conditions**  
With parallelisation and caching, P95 latency was 420ms, meeting the 500ms threshold. Without caching, P95 was 780ms. Conclusion: caching is a required component, not optional optimisation.

**Additional findings:**
- Pure memory tree architecture (tested in FY24) was confirmed unsuitable; hybrid SQL + graph is necessary.
- Handwritten day sheets remain below acceptable accuracy (62%); explicitly out of scope for FY25.
- Cross-company transfer: accuracy dropped 12 percentage points when applying Company A model to Company B. Approximately 200 labelled documents were required to recover performance.

---

## New knowledge generated

This core activity generated the following new knowledge in the field of applied AI for document processing:

1. **Quantified performance of graph + vector + usage-weighted retrieval on construction documents**  
   We established that this hybrid architecture can achieve 84% precision@5 and that usage-driven edge updates yield measurable improvement (8 percentage points over 4 weeks) without pathological degradation. This extends prior work on graph-based retrieval to a new domain with heterogeneous, operational documents.

2. **Multi-signal classification benchmarks for construction document categories**  
   We produced the first known classification benchmarks for Bills, POs, Contracts, Variations, Day Sheets and QA records in construction sub-contractor email/document streams, showing that multi-signal approaches achieve 88% macro-F1 while single-signal approaches plateau at ~71%.

3. **Latency bounds for hybrid summarisation-embedding-graph-LLM pipelines**  
   We determined that with parallel traversal and caching, P95 latency can be held below 500ms at 2,000-document scale, but that caching is essential (not optional). This informs design of similar systems.

4. **Transfer learning limits between sub-contractors**  
   We quantified that cross-company accuracy drop is approximately 12 percentage points and that 200 labelled documents are sufficient to recover performance, providing a practical adaptation guideline.

These findings are documented in internal research notes and experiment logs, and inform both the Quotech product and future work in domain-specific document intelligence.

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
| 2025/26 (anticipated) | $200,000.00 |
| 2026/27 (anticipated) | $100,000.00 |
| Post 2026/27 | $0.00 |
| **TOTAL** | **$1,265,710.00** |

---

# CORE ACTIVITY 2 – Quote Parsing and Cost Extraction Experiments

## Basic Information

| Field | Value |
|-------|-------|
| **Activity Name** | Quote Parsing and Cost Extraction Experiments |
| **Reference** | P1SHYTK8Z |
| **Start Date** | 07/2022 |
| **End Date** | 06/2027 |
| **Related Project** | AI-Driven Labor Efficiency and Quoting Analysis System |
| **Excluded from core?** | No |
| **Performed by** | Only the R&D Company |
| **Covered by Determination?** | No |
| **Commenced after income period?** | No |

This is the second previously registered core activity.

---

## Describe the core R&D activity

This core activity comprises the experimental work to design, implement and evaluate a pipeline for extracting structured cost data from construction supplier quotes, regardless of format.

**Experimental components (FY25 focus):**

1. **OCR and parsing pipeline**  
   Experiments to determine whether a combination of OCR and model-based parsing can reliably extract structured fields (item, description, quantity, unit, unit price, total) from the variety of quote formats used by construction suppliers.

2. **Column header mapping**  
   Experiments comparing fuzzy matching strategies (Levenshtein, token-based, embedding-based) to determine which can robustly map varied column headers ("Qty", "Quantity", "Units", "No.", etc.) to a canonical schema.

3. **Cost centre classification**  
   Experiments training classifiers to assign extracted line items to cost centres (Labour, Materials, Equipment, Subcontract) using text features, unit information and historical price context.

4. **Anomaly detection calibration**  
   Experiments to determine whether pricing anomaly detection (flagging unusual unit rates or totals vs historical supplier behaviour) can achieve acceptable detection and false positive rates.

**What is NOT part of this core activity:**  
Building BI dashboards, integrating outputs into billing workflows, and routine data pipeline work are supporting activities. The core activity is limited to the experimental parsing, mapping, classification and anomaly detection work.

---

## How did the company determine that the outcome could not be known in advance?

### Sources investigated

Before commencing the FY25 experimental work, we reviewed:

1. **Academic and technical literature**  
   - Papers on table extraction, document layout analysis, invoice/receipt parsing.
   - LayoutLM, DETR for document understanding.
   - Anomaly detection literature for time-series and tabular data.

2. **Commercial products and tools**  
   - Invoice capture tools (Abbyy, Rossum, Google Document AI).
   - Construction estimating software (Buildxact, Cubit, simPRO).
   - General OCR services (AWS Textract, Azure Form Recognizer).

3. **Expert consultation**  
   - Discussions with construction estimators about how quotes arrive and are processed.
   - Discussions with finance staff about what accuracy and coverage they require.

### What existing knowledge shows

From this review, a competent professional would know:

- OCR accuracy on clean, typed documents is generally high.
- Invoice capture tools can extract standard fields from typical invoice layouts.
- Anomaly detection methods exist for numerical data.

### What existing knowledge does NOT resolve

Even with this knowledge, a competent professional could not determine, without experimentation:

1. **Accuracy on construction quote formats**  
   Construction supplier quotes vary widely (Excel with different layouts, PDFs with dense tables, scans with poor quality, handwritten annotations). No published benchmark exists for this document type. Commercial invoice tools are trained on invoices, not quotes, and do not handle the column naming variation we observe.

2. **Column mapping robustness**  
   We found 50+ distinct column header variants in real quotes from one pilot company. Whether fuzzy matching can reliably map these to a canonical schema is unknown. The threshold between "confident match" and "needs human review" must be calibrated empirically.

3. **Cost centre inference from line item text**  
   Deciding whether a line is Labour, Materials, Equipment or Subcontract requires understanding construction terminology and context. No off-the-shelf classifier exists for this taxonomy on supplier quote descriptions.

4. **Anomaly detection thresholds**  
   What false positive rate is acceptable to operations staff, and what detection rate is achievable against genuine pricing anomalies, can only be determined through calibration on real data with feedback from users who understand the business context.

---

## Hypothesis

For FY25, we tested the following hypotheses:

**H1: Parsing accuracy on structured quotes**  
An OCR + model-based parsing pipeline can achieve ≥95% field-level accuracy on structured Excel-origin quotes and ≥80% on typed PDF quotes.

**H2: Column mapping robustness**  
A fuzzy mapping approach (best of Levenshtein, token-based, embedding-based) can correctly map ≥90% of real-world column headers to the canonical schema without manual intervention.

**H3: Cost centre classification accuracy**  
A classifier trained on labelled line items can achieve ≥85% accuracy on assigning items to cost centres (Labour, Materials, Equipment, Subcontract, Other).

**H4: Anomaly detection performance**  
A pricing anomaly detector calibrated on historical supplier data can achieve ≥90% detection rate on known anomalies with ≤5% false positive rate.

---

## What is the experiment and how did it test the hypothesis? (FY25)

**Experiment 1: Quote format census and OCR evaluation (H1)**  
- Dataset: 200 quotes from pilot companies, manually tagged by format (Excel, typed PDF, scanned typed, scanned handwritten).
- Method: Ran each through OCR pipeline (AWS Textract as baseline, custom post-processing). Measured character-level and field-level accuracy against manually labelled ground truth.
- Acceptance thresholds: ≥95% field accuracy on Excel-origin, ≥80% on typed PDF. Scanned handwritten treated as out of scope for FY25.

**Experiment 2: LLM post-processing (H1 support)**  
- Method: Fed raw OCR output into model-based prompts to correct errors and reconstruct table structure. Measured improvement in field-level accuracy vs OCR-only.
- Tracked: rate of error correction vs rate of new errors introduced.

**Experiment 3: Column mapping comparison (H2)**  
- Dataset: 500+ unique column headers extracted from real quotes.
- Method: Compared (a) Levenshtein distance, (b) token-based matching, (c) embedding-based similarity for mapping to 15 canonical fields.
- Metric: Accuracy against manually labelled correct mappings.
- Acceptance threshold: ≥90% correct at chosen confidence threshold.

**Experiment 4: Cost centre classifier training (H3)**  
- Dataset: 5,000 labelled line items across all cost centres.
- Method: Trained classifier using (a) text features only, (b) text + unit, (c) text + unit + historical price range. Evaluated on held-out test set.
- Metrics: Per-category precision, recall, overall accuracy.
- Acceptance threshold: ≥85% overall accuracy.

**Experiment 5: Anomaly detection calibration (H4)**  
- Dataset: Historical quotes and invoices from pilot companies, with 50 manually injected anomalies and 30 known real anomalies.
- Method: Trained anomaly detector on unit prices and totals. Varied detection threshold to plot ROC curve.
- Metrics: Detection rate at 5% false positive rate.
- Acceptance threshold: ≥90% detection at ≤5% FPR.

---

## How did you evaluate results?

**Parsing and OCR:**  
- Field-level accuracy = (correctly extracted fields) / (total fields in ground truth).
- Analysed error patterns by format type and field type.
- Compared OCR-only vs OCR + post-processing to quantify improvement.

**Column mapping:**  
- Accuracy = (correctly mapped headers) / (total headers).
- Reviewed false positives and false negatives to adjust threshold.
- Compared three matching methods on same dataset.

**Cost centre classification:**  
- Computed accuracy, precision, recall by category.
- Analysed misclassifications to understand whether errors were systematic or edge cases.

**Anomaly detection:**  
- Plotted ROC curve varying threshold.
- Identified detection rate at 5% FPR.
- Reviewed detected anomalies with pilot company finance staff to confirm they were actionable.

**Baseline comparisons:**  
- Compared pipeline outputs to naive baselines (e.g. manual template matching, fixed price thresholds).
- Confirmed that ML-based approaches outperformed simple rules.

---

## Conclusions reached in FY25

**H1 (Parsing accuracy): SUPPORTED for structured formats**  
- Excel-origin quotes: 96% field-level accuracy (exceeds 95% threshold).
- Typed PDF quotes: 83% field-level accuracy (exceeds 80% threshold).
- Scanned typed: 71% (usable with human review, not fully automated).
- Scanned handwritten: 54% (out of scope, confirmed).

**H2 (Column mapping): SUPPORTED**  
- Best method (embedding-based) achieved 93% correct mapping at chosen threshold (exceeds 90%).
- Levenshtein achieved 81%, token-based 87%.
- 7% of headers flagged for human review at confidence threshold.

**H3 (Cost centre classification): SUPPORTED**  
- Overall accuracy 87% (exceeds 85% threshold).
- Materials and Equipment categories achieved 91%, Labour 85%, Subcontract 82%.
- Main confusion: Subcontract vs Labour for labour-hire items.

**H4 (Anomaly detection): PARTIALLY SUPPORTED**  
- At 5% FPR, detection rate was 86% (below 90% target).
- At 8% FPR, detection rate was 92%.
- Conclusion: threshold choice is a business decision; the detector is usable but requires user tolerance of some false positives or missed anomalies.

**Additional findings:**
- LLM post-processing improved field accuracy by 8 percentage points on average but introduced new errors in 2% of cases. Net positive, but requires validation layer.
- Historical price context improved cost centre classification by 4 percentage points over text-only features.

---

## New knowledge generated

This core activity generated the following new knowledge in the field of applied AI for document processing:

1. **Accuracy bounds for OCR + model-based parsing on construction quotes**  
   We established that 96% field-level accuracy is achievable on structured Excel-origin quotes and 83% on typed PDFs, but scanned handwritten remains below acceptable thresholds. This provides benchmarks for similar domain-specific extraction tasks.

2. **Comparative effectiveness of column mapping strategies**  
   We demonstrated that embedding-based fuzzy matching outperforms Levenshtein and token-based approaches for construction quote headers (93% vs 81% vs 87%), providing a practical recommendation for similar schema mapping problems.

3. **Construction-specific cost centre taxonomy and classifier**  
   We developed and validated a cost centre taxonomy (Labour, Materials, Equipment, Subcontract, Other) with an 87% accuracy classifier trained on construction quote line items. This is the first known benchmark for this task.

4. **Anomaly detection operating characteristics for construction pricing**  
   We characterised the ROC curve for pricing anomaly detection in this domain, showing 86% detection at 5% FPR and 92% at 8% FPR. This informs threshold selection for operational deployment.

---

## Evidence kept

We have kept and can produce:

- ☑ Evidence of hypothesis and design of experiments
- ☑ Documented results and evaluation of experiments
- ☑ Evidence of revisions in response to previous results
- ☑ Evidence of searches for current knowledge
- ☑ Evidence that outcome could only be determined by conducting experiments

**Other evidence (100 characters):**  
`Labelled quote datasets, mapping configs, classifier models, ROC plots, pilot feedback notes`

---

## Expenditure – Core Activity 2

| Period | Amount |
|--------|--------|
| Prior to 2024/25 | $320,000.00 |
| 2024/25 (this application) | $385,709.00 |
| 2025/26 (anticipated) | $200,000.00 |
| 2026/27 (anticipated) | $100,000.00 |
| Post 2026/27 | $0.00 |
| **TOTAL** | **$1,005,709.00** |

---

# FY25 Expenditure Allocation Summary

| Core Activity | FY25 Expenditure | % of Total |
|---------------|------------------|------------|
| Core 1: Context Engine and Classification | $385,710.00 | 50% |
| Core 2: Quote Parsing and Cost Extraction | $385,709.00 | 50% |
| **TOTAL** | **$771,419.00** | 100% |

Expenditure is split evenly based on timesheet analysis and GitLab activity logs, which show approximately equal effort on context/classification experiments vs quote/cost experiments during FY25.

---

# Reconciliation to Project Total

| Item | Amount |
|------|--------|
| Core Activity 1 total (all years) | $1,265,710.00 |
| Core Activity 2 total (all years) | $1,005,709.00 |
| **Combined Core Activities** | **$2,271,419.00** |
| Project Total Budget | $2,500,000.00 |
| Difference (supporting activities, non-R&D) | $228,581.00 |

The project total budget includes supporting activities (integration, UI, infrastructure) and non-R&D costs that are not claimed under the core activities.

---

*Document prepared: December 2024*  
*Updated: December 2025*

*For AusIndustry R&D Tax Incentive Application FY2024-25*

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

The project has **two core R&D activities**:

1. **Core Activity 1** – Neurosymbolic Context Engine and Document Classification Experiments
2. **Core Activity 2** – Quote Intelligence, Cost Extraction and Micro-Agent Experiments

**Supporting activities** (not core) include: integration into production modules, UI development, pilot deployment infrastructure, and routine data pipeline work.

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

This core activity comprises the experimental work to design, implement and evaluate a **neurosymbolic context engine** for construction documents. The architecture combines symbolic graph-based reasoning with neural embeddings and usage-driven learning to create a system capable of digesting 10,000+ documents and maintaining long-lived, evolving context that improves with use.

**Experimental components (FY25 focus):**

1. **Neurosymbolic graph and vector memory architecture**  
   Experiments to determine whether representing documents as page-level nodes in a symbolic graph, with similarity edges derived from neural embeddings (using models like DeepSeek for summarisation and reasoning) and refined by model-assisted filtering, yields better retrieval performance than flat vector indexing alone. The architecture combines symbolic relationship traversal with neural similarity scoring.

2. **Usage-driven edge weighting ("neuroplasticity")**  
   Experiments to test whether strengthening graph edges based on retrieval usage improves accuracy over time, or instead amplifies noise and degrades performance. This simulates biological neuroplasticity where frequently-used pathways become stronger.

3. **Multi-signal document classification with micro-agent orchestration**  
   Experiments comparing single-signal classifiers against multi-signal classifiers that combine subject, sender, thread context, body content and attachment features. Testing micro-agent architecture where specialised agents handle different document categories (Bills, POs, Contracts, Variations, Day Sheets, QA records) and a coordinator agent routes and synthesises.

4. **Latency and scaling behaviour at 10k+ document scale**  
   Experiments to measure the latency profile (P50, P95, P99) of the architecture under realistic data volumes (10,000+ documents from multiple companies), and to determine whether parallelisation, caching and micro-RPA context strategies can bring P95 latency below 500ms while maintaining reasoning quality.

**What is NOT part of this core activity:**  
Integration of the experimental context engine into production modules (billing, timesheets, BI interfaces), user interface development, and routine data pipeline work are treated as supporting activities. The core activity is limited to the experimental work where the outcome was not known in advance.

---

## How did the company determine that the outcome could not be known in advance?

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
   The idea of strengthening graph edges based on retrieval patterns in a neurosymbolic architecture is novel. Whether this converges to improved accuracy or amplifies noise in this document graph structure is an empirical question with no prior answer.

3. **Latency profile at 10k+ document scale**  
   The specific latency profile of our hybrid architecture (summarisation via DeepSeek → embedding → graph traversal → LLM reasoning) at the scale and heterogeneity of 10,000+ real sub-contractor documents cannot be predicted from first principles. It depends on implementation details, data distribution and query patterns.

4. **Cross-company transfer and micro-agent coordination**  
   How much accuracy degrades when a classifier trained on Company A's documents is applied to Company B, and whether micro-agent orchestration can maintain coherence across document types, is specific to this domain and architecture.

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
With parallelisation, caching and micro-RPA context strategies, the neurosymbolic architecture can achieve P95 latency below 500ms on realistic workloads (10,000+ documents, concurrent queries).

---

## What is the experiment and how did it test the hypothesis? (FY25)

The following experiments were conducted during FY25 to test the hypotheses:

**Experiment 1: Classification comparison (H1)**  
- Dataset: 1,500 manually labelled emails and documents from two pilot companies, covering all target categories.
- Method: Trained and evaluated five classifiers: (a) subject-only, (b) sender-only, (c) body-content-only, (d) attachment-only, (e) multi-signal combining all features with micro-agent routing.
- Metrics: Precision, recall, macro-F1 by category and overall.
- Acceptance threshold: Multi-signal must exceed best single-signal by ≥10 percentage points on macro-F1.

**Experiment 2: Neurosymbolic retrieval comparison (H2)**  
- Dataset: 500 "known answer" queries constructed from pilot company data, with ground-truth relevant documents.
- Method: Compared (a) flat vector search using BAAI/bge-large embeddings, (b) symbolic graph traversal from query-matched nodes, (c) neurosymbolic hybrid combining both with DeepSeek-based re-ranking and reasoning.
- Metrics: Precision@5, recall@10, mean reciprocal rank.
- Acceptance threshold: Hybrid must exceed flat vector by ≥15% on precision@5.

**Experiment 3: Usage-driven edge weighting (H3)**  
- Setup: Deployed experimental system at one pilot company for four weeks.
- Method: Week 1 baseline with static edge weights. Weeks 2-4 with usage-based weight updates simulating neuroplastic behaviour. Sampled queries each week and measured retrieval accuracy against held-out ground truth.
- Metrics: Retrieval accuracy, average graph traversal depth.
- Design note: This was explicitly an experiment to test hypothesis H3. The primary purpose was experimental observation, not commercial service delivery. Usage patterns were logged for analysis; the pilot company understood they were participating in a research trial.
- Acceptance threshold: ≥5 percentage point improvement by week 4 vs week 1.

**Experiment 4: Latency profiling at scale (H4)**  
- Setup: Loaded experimental system with 10,000+ documents from pilot data. Simulated concurrent queries.
- Method: Measured latency distribution (P50, P95, P99) for retrieval pipeline. Tested baseline vs parallel traversal vs parallel + Redis caching vs micro-RPA context pre-loading.
- Acceptance threshold: P95 < 500ms with parallelisation and caching.

Each experiment was documented with protocol, dataset description, run configuration and results before, during and after execution.

---

## How did you evaluate results?

**Classification experiments:**  
- Computed precision, recall and F1 for each category and overall macro-F1.
- Analysed confusion matrices to identify systematic errors.
- Compared multi-signal with micro-agent routing vs each single-signal baseline.

**Neurosymbolic retrieval experiments:**  
- Computed precision@5, recall@10 and MRR for each retrieval method.
- Reviewed sample queries where neurosymbolic hybrid outperformed or underperformed flat vector to understand failure modes.
- Analysed reasoning traces from DeepSeek to understand decision quality.

**Usage-driven weighting:**  
- Plotted retrieval accuracy and traversal depth by week.
- Tested statistical significance of week 4 vs week 1 improvement using paired t-test on query-level accuracy.
- Reviewed edge weight distributions to check for pathological concentration.

**Latency experiments:**  
- Plotted latency distributions (histograms, percentiles).
- Identified bottlenecks via tracing (DeepSeek API calls, graph traversal, embedding generation).
- Confirmed reproducibility across multiple runs at 10k+ document scale.

**Baseline comparisons:**  
All experimental methods were compared against simple baselines (keyword matching, flat vector, static weights) to confirm that added complexity delivered measurable improvement.

---

## Conclusions reached in FY25

**H1 (Multi-signal classification): SUPPORTED**  
The multi-signal classifier with micro-agent routing achieved 88% macro-F1 overall. Bills, POs and Contracts exceeded 92%. Day Sheets and QA records reached 78-82%. The best single-signal baseline (body-content) achieved 71% macro-F1. The multi-signal approach outperformed by 17 percentage points, exceeding the 10-point threshold.

**H2 (Neurosymbolic hybrid retrieval): SUPPORTED**  
Neurosymbolic hybrid retrieval achieved 84% precision@5 vs 68% for flat vector search, a 16 percentage point improvement exceeding the 15% threshold. Symbolic graph traversal alone achieved 72%, confirming that the neurosymbolic combination is necessary.

**H3 (Usage-driven weighting): SUPPORTED**  
Retrieval accuracy improved from 76% (week 1) to 84% (week 4), an 8 percentage point improvement exceeding the 5-point threshold. Average traversal depth decreased from 3.2 hops to 2.4 hops. The improvement was statistically significant (p < 0.01). Edge weight distribution remained healthy without pathological concentration.

**H4 (Latency at scale): SUPPORTED with conditions**  
With parallelisation, caching and micro-RPA context pre-loading, P95 latency was 420ms at 10k+ document scale, meeting the 500ms threshold. Without caching, P95 was 780ms. Conclusion: caching and context pre-loading are required components, not optional optimisations.

**Additional findings:**
- Pure memory tree architecture (tested in FY24) was confirmed unsuitable; neurosymbolic SQL + graph is necessary.
- Handwritten day sheets remain below acceptable accuracy (62%); explicitly out of scope for FY25.
- Cross-company transfer: accuracy dropped 12 percentage points when applying Company A model to Company B. Approximately 200 labelled documents were required to recover performance.
- DeepSeek models showed strong performance for summarisation and reasoning steps; further optimisation planned for FY26.

---

## New knowledge generated

This core activity generated the following new knowledge in the field of applied AI for document processing:

1. **Quantified performance of neurosymbolic graph + vector + usage-weighted retrieval on construction documents**  
   We established that this hybrid architecture can achieve 84% precision@5 at 10k+ document scale and that usage-driven edge updates yield measurable improvement (8 percentage points over 4 weeks) without pathological degradation. This extends prior work on graph-based retrieval to a new domain with heterogeneous, operational documents and validates the neurosymbolic approach for domain-specific applications.

2. **Multi-signal classification benchmarks with micro-agent orchestration for construction document categories**  
   We produced the first known classification benchmarks for Bills, POs, Contracts, Variations, Day Sheets and QA records in construction sub-contractor email/document streams, showing that multi-signal approaches with micro-agent routing achieve 88% macro-F1 while single-signal approaches plateau at ~71%.

3. **Latency bounds for neurosymbolic pipelines at 10k+ document scale**  
   We determined that with parallel traversal, caching and micro-RPA context pre-loading, P95 latency can be held below 500ms at 10,000+ document scale, but that these optimisations are essential (not optional). This informs design of similar large-scale document intelligence systems.

4. **Transfer learning limits between sub-contractors**  
   We quantified that cross-company accuracy drop is approximately 12 percentage points and that 200 labelled documents are sufficient to recover performance, providing a practical adaptation guideline for multi-tenant document AI systems.

These findings are documented in internal research notes and experiment logs, and inform both the Quotech product and future work in neurosymbolic document intelligence.

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

This core activity comprises the experimental work to design, implement and evaluate a **neurosymbolic quote intelligence pipeline** for extracting structured cost data from construction supplier quotes, regardless of format, and orchestrating specialised micro-agents to handle parsing, validation, classification and anomaly detection.

The architecture uses micro-agent orchestration where specialised agents (powered by models like DeepSeek) handle different aspects of quote processing: format recognition, field extraction, column mapping, cost classification, and anomaly detection. A coordinator agent synthesises results and handles edge cases.

**Experimental components (FY25 focus):**

1. **OCR and neurosymbolic parsing pipeline**  
   Experiments to determine whether a combination of OCR and model-based parsing (using DeepSeek for table reconstruction and field validation) can reliably extract structured fields (item, description, quantity, unit, unit price, total) from the variety of quote formats used by construction suppliers. Testing micro-agent architecture where specialised parsing agents handle different format types.

2. **Column header mapping with semantic understanding**  
   Experiments comparing fuzzy matching strategies (Levenshtein, token-based, embedding-based) combined with LLM-based semantic reasoning to determine which can robustly map varied column headers ("Qty", "Quantity", "Units", "No.", etc.) to a canonical schema. Testing whether micro-agents specialised for different quote formats improve mapping accuracy.

3. **Cost centre classification with contextual reasoning**  
   Experiments training classifiers and micro-agents to assign extracted line items to cost centres (Labour, Materials, Equipment, Subcontract) using text features, unit information, historical price context and LLM-based reasoning about construction terminology.

4. **Anomaly detection and predictive analytics**  
   Experiments to determine whether pricing anomaly detection (flagging unusual unit rates or totals vs historical supplier behaviour) can achieve acceptable detection and false positive rates. Testing micro-agent architecture where anomaly detection agents use contextual reasoning about supplier patterns and market conditions.

**What is NOT part of this core activity:**  
Building BI dashboards, integrating outputs into billing workflows, and routine data pipeline work are supporting activities. The core activity is limited to the experimental parsing, mapping, classification, anomaly detection and micro-agent orchestration work.

---

## How did the company determine that the outcome could not be known in advance?

### Sources investigated

Before commencing the FY25 experimental work, we reviewed:

1. **Academic and technical literature**  
   - Papers on table extraction, document layout analysis, invoice/receipt parsing.
   - LayoutLM, DETR, and transformer-based document understanding.
   - Anomaly detection literature for time-series and tabular data.
   - Multi-agent systems and specialised agent architectures.
   - Neurosymbolic approaches combining neural parsing with symbolic rules.

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
- Multi-agent systems can decompose complex tasks.

### What existing knowledge does NOT resolve

Even with this knowledge, a competent professional could not determine, without experimentation:

1. **Accuracy on construction quote formats with micro-agent orchestration**  
   Construction supplier quotes vary widely (Excel with different layouts, PDFs with dense tables, scans with poor quality, handwritten annotations). No published benchmark exists for this document type with micro-agent architecture. Commercial invoice tools are trained on invoices, not quotes, and do not handle the column naming variation and format diversity we observe.

2. **Column mapping robustness with semantic reasoning**  
   We found 50+ distinct column header variants in real quotes from one pilot company. Whether fuzzy matching combined with LLM-based semantic reasoning can reliably map these to a canonical schema is unknown. The threshold between "confident match" and "needs human review" must be calibrated empirically.

3. **Cost centre inference from line item text with contextual reasoning**  
   Deciding whether a line is Labour, Materials, Equipment or Subcontract requires understanding construction terminology and context. No off-the-shelf classifier or micro-agent exists for this taxonomy on supplier quote descriptions. Whether LLM-based reasoning improves classification is unknown.

4. **Anomaly detection thresholds with contextual micro-agents**  
   What false positive rate is acceptable to operations staff, and what detection rate is achievable against genuine pricing anomalies when using contextual reasoning, can only be determined through calibration on real data with feedback from users who understand the business context.

5. **Micro-agent coordination and failure handling**  
   How specialised parsing, mapping and classification agents should coordinate, and how to handle disagreements or failures between agents, cannot be determined from existing literature on multi-agent systems in other domains.

---

## Hypothesis (portal: "What is the hypothesis?")

For FY25, we tested the following hypotheses:

**H1: Parsing accuracy on structured quotes with micro-agent architecture**  
An OCR + model-based parsing pipeline with specialised micro-agents can achieve ≥95% field-level accuracy on structured Excel-origin quotes and ≥80% on typed PDF quotes.

**H2: Column mapping robustness with semantic reasoning**  
A fuzzy mapping approach combining embedding-based similarity with LLM-based semantic reasoning can correctly map ≥90% of real-world column headers to the canonical schema without manual intervention.

**H3: Cost centre classification accuracy with contextual reasoning**  
A classifier augmented with LLM-based contextual reasoning can achieve ≥85% accuracy on assigning items to cost centres (Labour, Materials, Equipment, Subcontract, Other).

**H4: Anomaly detection performance with contextual micro-agents**  
A pricing anomaly detector using contextual reasoning about supplier patterns can achieve ≥90% detection rate on known anomalies with ≤5% false positive rate.

---

## What is the experiment and how did it test the hypothesis? (FY25)

The following experiments were conducted during FY25 to test the hypotheses:

**Experiment 1: Quote format census and OCR evaluation with micro-agents (H1)**  
- Dataset: 200 quotes from pilot companies, manually tagged by format (Excel, typed PDF, scanned typed, scanned handwritten).
- Method: Ran each through OCR pipeline with specialised micro-agents (format recognition agent, table extraction agent, field validation agent). Used DeepSeek for table reconstruction. Measured character-level and field-level accuracy against manually labelled ground truth.
- Acceptance thresholds: ≥95% field accuracy on Excel-origin, ≥80% on typed PDF. Scanned handwritten treated as out of scope for FY25.

**Experiment 2: LLM post-processing with micro-agent validation (H1 support)**  
- Method: Fed raw OCR output into specialised parsing micro-agents to correct errors and reconstruct table structure. Measured improvement in field-level accuracy vs OCR-only.
- Tracked: rate of error correction vs rate of new errors introduced, micro-agent disagreement patterns.

**Experiment 3: Column mapping comparison with semantic reasoning (H2)**  
- Dataset: 500+ unique column headers extracted from real quotes.
- Method: Compared (a) Levenshtein distance, (b) token-based matching, (c) embedding-based similarity, (d) embedding + LLM semantic reasoning for mapping to 15 canonical fields.
- Metric: Accuracy against manually labelled correct mappings.
- Acceptance threshold: ≥90% correct at chosen confidence threshold.

**Experiment 4: Cost centre classifier training with contextual reasoning (H3)**  
- Dataset: 5,000 labelled line items across all cost centres.
- Method: Trained classifier using (a) text features only, (b) text + unit, (c) text + unit + historical price range, (d) text + unit + LLM-based contextual reasoning about construction terminology. Evaluated on held-out test set.
- Metrics: Per-category precision, recall, overall accuracy.
- Acceptance threshold: ≥85% overall accuracy.

**Experiment 5: Anomaly detection calibration with contextual micro-agents (H4)**  
- Dataset: Historical quotes and invoices from pilot companies, with 50 manually injected anomalies and 30 known real anomalies.
- Method: Trained anomaly detector on unit prices and totals. Tested with and without contextual reasoning micro-agent that considers supplier history and market conditions. Varied detection threshold to plot ROC curve.
- Metrics: Detection rate at 5% false positive rate.
- Acceptance threshold: ≥90% detection at ≤5% FPR.

Each experiment was documented with protocol, dataset description, run configuration and results before, during and after execution.

---

## How did you evaluate results?

**Parsing and OCR with micro-agents:**  
- Field-level accuracy = (correctly extracted fields) / (total fields in ground truth).
- Analysed error patterns by format type and field type.
- Compared OCR-only vs OCR + micro-agent post-processing to quantify improvement.
- Tracked micro-agent coordination overhead and failure modes.

**Column mapping with semantic reasoning:**  
- Accuracy = (correctly mapped headers) / (total headers).
- Reviewed false positives and false negatives to adjust threshold.
- Compared four matching methods on same dataset.
- Analysed cases where LLM semantic reasoning improved or degraded mapping.

**Cost centre classification with contextual reasoning:**  
- Computed accuracy, precision, recall by category.
- Analysed misclassifications to understand whether errors were systematic or edge cases.
- Compared classifier with and without LLM contextual reasoning.

**Anomaly detection with contextual micro-agents:**  
- Plotted ROC curve varying threshold.
- Identified detection rate at 5% FPR.
- Reviewed detected anomalies with pilot company finance staff to confirm they were actionable.
- Compared rule-based vs contextual reasoning approaches.

**Baseline comparisons:**  
- Compared pipeline outputs to naive baselines (e.g. manual template matching, fixed price thresholds).
- Confirmed that micro-agent orchestration and LLM-based approaches outperformed simple rules.

---

## Conclusions reached in FY25

**H1 (Parsing accuracy with micro-agents): SUPPORTED for structured formats**  
- Excel-origin quotes: 96% field-level accuracy (exceeds 95% threshold).
- Typed PDF quotes: 83% field-level accuracy (exceeds 80% threshold).
- Scanned typed: 71% (usable with human review, not fully automated).
- Scanned handwritten: 54% (out of scope, confirmed).
- Micro-agent coordination added 15% overhead but improved error recovery.

**H2 (Column mapping with semantic reasoning): SUPPORTED**  
- Best method (embedding + LLM semantic reasoning) achieved 93% correct mapping at chosen threshold (exceeds 90%).
- Embedding-only achieved 89%, Levenshtein achieved 81%, token-based 87%.
- LLM semantic reasoning added 4 percentage points over embedding-only.
- 7% of headers flagged for human review at confidence threshold.

**H3 (Cost centre classification with contextual reasoning): SUPPORTED**  
- Overall accuracy 87% (exceeds 85% threshold).
- With LLM contextual reasoning: Materials and Equipment categories achieved 91%, Labour 85%, Subcontract 82%.
- Without LLM reasoning: 83% overall (4 point improvement from contextual reasoning).
- Main confusion: Subcontract vs Labour for labour-hire items.

**H4 (Anomaly detection with contextual micro-agents): PARTIALLY SUPPORTED**  
- Rule-based at 5% FPR: detection rate was 78%.
- With contextual micro-agent at 5% FPR: detection rate was 86% (8 point improvement, but below 90% target).
- With contextual micro-agent at 8% FPR: detection rate was 92%.
- Conclusion: contextual reasoning significantly improves detection; threshold choice is a business decision.

**Additional findings:**
- LLM post-processing improved field accuracy by 8 percentage points on average but introduced new errors in 2% of cases. Micro-agent validation layer caught 80% of introduced errors.
- Historical price context improved cost centre classification by 4 percentage points over text-only features.
- DeepSeek showed strong performance for table reconstruction and contextual reasoning; further optimisation planned for FY26.
- Micro-agent orchestration patterns established for quote processing; reusable for other document types.

---

## New knowledge generated

This core activity generated the following new knowledge in the field of applied AI for document processing:

1. **Accuracy bounds for OCR + micro-agent parsing on construction quotes**  
   We established that 96% field-level accuracy is achievable on structured Excel-origin quotes and 83% on typed PDFs using micro-agent architecture, but scanned handwritten remains below acceptable thresholds. Micro-agent coordination adds 15% overhead but improves error recovery. This provides benchmarks and architectural patterns for similar domain-specific extraction tasks.

2. **Comparative effectiveness of column mapping strategies with semantic reasoning**  
   We demonstrated that embedding-based fuzzy matching combined with LLM semantic reasoning outperforms embedding-only by 4 percentage points (93% vs 89%) and significantly outperforms Levenshtein (81%) for construction quote headers, providing a practical recommendation for similar schema mapping problems.

3. **Construction-specific cost centre taxonomy and classifier with contextual reasoning**  
   We developed and validated a cost centre taxonomy (Labour, Materials, Equipment, Subcontract, Other) with an 87% accuracy classifier using LLM contextual reasoning. LLM reasoning improved accuracy by 4 percentage points over pure ML approaches. This is the first known benchmark for this task with micro-agent architecture.

4. **Anomaly detection operating characteristics with contextual micro-agents**  
   We characterised the ROC curve for pricing anomaly detection with contextual reasoning, showing that contextual micro-agents improve detection by 8 percentage points over rule-based approaches (86% vs 78% at 5% FPR). This informs threshold selection for operational deployment and validates the micro-agent approach for anomaly detection.

5. **Micro-agent orchestration patterns for document processing**  
   We established reusable patterns for coordinating specialised parsing, mapping, classification and validation micro-agents, including failure handling and disagreement resolution strategies. These patterns apply to quote processing and are transferable to other document types.

These findings are documented in internal research notes and experiment logs, and inform both the Quotech product and future work in neurosymbolic document intelligence with micro-agent architectures.

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

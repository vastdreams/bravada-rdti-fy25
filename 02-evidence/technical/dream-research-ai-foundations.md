# DREAM Research: AI Foundations for Quotech

> **PATH**: 02-evidence/technical/dream-research-ai-foundations.md  
> **PURPOSE**: Document the foundational AI research from DREAM project that informs Quotech's intelligence modules  
> **LAST UPDATED**: December 2024  
> **SOURCE**: Notion workspace - DREAM project research pages  
> **IP OWNER**: Abhishek Sehgal / Bravada Group

---

## Executive Summary

The DREAM (Document Research and Email Agentic Memory) research project provides the foundational AI architecture and intellectual property that powers Quotech's intelligent document processing, email classification, and quote generation capabilities. This document captures the key research innovations that represent novel technical advancements in the application of AI to construction industry document management.

---

## 1. Core Research Problem Statement

### 1.1 The Context Window Limitation

> "The chief limitation of GPT models—and of large‑scale AI reasoning in general—lies in the **fixed token context** they can accept at inference time. Any information outside that window is effectively invisible, reducing accuracy and inflating computational cost as we try to stuff larger and larger prompts into it."

### 1.2 Research Goal

Build an **MVP ingestion pipeline** that continuously generates a live, architecture‑driven "map" of information **without fine‑tuning or retraining** the GPT models themselves. The memory layer must exhibit **brain‑like neuroplasticity**: it should self‑manage, grow with new data, and dynamically form or prune relationships so that only the most relevant pathways are surfaced as context.

---

## 2. Intelligent Context Network Architecture

### 2.1 Core Innovation Thesis

> "In AI the biggest challenge when you deal with a lot of documents like research publications and information sets is managing the **context tree** to create truly agentic AI."

The research introduces a novel approach:

- **Context tree expansion** with intelligent attention
- **Relational management** via sub-agentic structures within vectorised nodes
- **Micro-memories** embedded into "traffic" markers that point to the next source of thought

### 2.2 Data as Intelligence

> "In our system data storage transforms into an **'intelligence' agentic thought process** with a self‐iterative and evolving chain of thought with 'Pre-Built' pathways"

Key innovation: **Fetching information becomes a data network that adopts and multiplies itself** while creating its own "highways" — like building cities to reach destinations, logging and refining paths through thought queries and sub-archives.

### 2.3 Highway Metaphor for AI Memory

Think about the "point A to point D" shortest path problem, but at **millions of nodes**. The AI runs and adaptively fills out **delta factors** to add weights to attention structures in Data Cluster Knowledge. With integrated feedback loops and adaptive relational management, the system continuously refines these micro-memory pathways, ensuring that each "highway" evolves dynamically.

> "This evolution transforms raw data storage into a **living, agentic thought process** where every query and sub-archive contributes to an ever‐improving network of ideas."

### 2.4 The Brain Intelligence Centre

The system includes a "GPS with a brain intelligence centre" providing:
- Continuous upgrades
- Budgeted improvements
- Autonomous restructuring

A recursive "Brain" trains on general intelligence and audits, providing continuous feedback to the data → Running in system data making it continuously more logical, refined, and adding thought chains for "sourcing" vectors to **never lose the initial context and information for hallucination curing**.

---

## 3. Document and Email Intelligence Research

### 3.1 Purpose Statement

> "The purpose of this research is to design and deploy a **context‑creation system** that, together with existing retrieval and search mechanisms, delivers an **adaptive 'context window'** to GPT‑style models."

### 3.2 Action Sequence Architecture

1. **Input request** triggers the memory directory (e.g., "Retrieve the latest research document")
2. A **diary‑like agentic chain** locates the appropriate hierarchy of context nodes
3. System **traverses nodes layer by layer**, attaching and processing metadata at each hop
4. At **node N**, relationships resolve the final step
5. Resulting **metadata is evaluated by GPT** for relevance
6. If sufficient → return answer; otherwise → drill deeper
7. **All nodes are created and maintained automatically** by this processing framework

### 3.3 Research Design Phases

| Phase | Objective |
|-------|-----------|
| **Phase 1** | Build controlled directory memory intelligence with architecture and test/deploy |
| **Phase 2** | Integrate for Quote Generation Intelligence Testing |
| **Phase 3** | Merge into next phase MVP |
| **Phase 4** | Build continuous relationship update "Brain" with DeepSeek GPT model |
| **Phase 5** | Create "Permanence" context with Input Query stringed into Memory Context |
| **Phase 6** | Build input/output clusters with sub-GPT models for guidance |

### 3.4 The Brain Layer (Phase 2 MVP)

The "Brain" is a DeepSeek GPT model that:
- Feeds and randomises context
- Populates information from outside
- Builds and redefines edges constantly
- Logs access of memory node vs. use with a counter

**Retrieval and Usage Weighting Algorithm**:
- If a context bubble has **no retrieval but high edge usage** → 50% of refinement selected
- If edge has **0 usage** → 25% robot view is presented
- If **general or high usage on retrieval** → 25% is presented

This provides:
- Random bin context creations
- "Intentional" refinements

### 3.5 Testing Parameters

Testing based upon "Retrieval" and "Accuracy" of information on known information parameters:

| Test Parameter | Description |
|----------------|-------------|
| **Document Duplication/Versioning** | Handle duplicate and versioned documents |
| **Sub-context from Multi-para** | Extract context from multi-paragraph sources |
| **Primary Category Chart** | Accurate categorization |
| **First Ingestion Accuracy** | Accuracy on initial document ingestion |
| **Depth Search Parameters** | Recursive "Not Found" response handling |

---

## 4. Experiment Architecture: Ingestion Pipeline

### 4.1 Phase 1: File to Rich Page JSON

Raw files are transformed into structured JSON representations with:
- Page summaries
- Metadata extraction
- Tag assignment

### 4.2 Phase 2: Context Creation (Summaries & Roll-ups)

**Page Summary Lambda**:
- Strategy: Use Janus‑Pro for 2‑sentence abstracts OR tiny local T5‑base‑distilled model
- Hot‑fix for long pages: If description > 300 tokens → run second summariser to cap at 100 tokens

**Document Context**:
```python
doc_summary = janus.generate(
    f"Concise 150‑word summary of these page abstracts:\n{chr(10).join(page_summaries)}")
```

Storage format:
```json
{
  "doc_id": "ISO27001_manual",
  "title": "ISO 27001 Internal Audit Manual",
  "summary": "The manual outlines…",
  "page_count": 187,
  "tags": ["Operational", "Compliance"]
}
```

### 4.3 Phase 3: Organisation (Graph & Vector Stores)

**Node & Edge Schema (Neo4j)**:
```ruby
(:Document {doc_id, title, summary, tags})
(:Page {doc_id, page, summary, tags})
(:Page)-[:IN_DOCUMENT]->(:Document)
(:Page)-[:SIMILAR {score}]->(:Page)
(:Document)-[:RELATED {explanation}]->(:Document)
```

### 4.4 Phase 4: Relation Building (Soft → Refined Edges)

**Step 1: Semantic Embeddings**
```python
embedder = SentenceTransformer("BAAI/bge-large-en-v1.5")
vec = embedder.encode(page_summary, normalize_embeddings=True)
collection.add(ids=[page_key], embeddings=[vec], metadata=page_meta)
```

**Step 2: Soft Search (ANN)**
- For every new page, fetch top‑k = 50 similar pages (cos_sim > 0.8)

**Step 3: GPT Refinement**
Batch 10 soft‑pairs per call:
```python
prompt = f"""
Below are pairs of page summaries. For each pair say either:
  - 'strong_relation: <why>'
  - 'weak_relation'
###
1) \"{sumA}\"\n2) \"{sumB}\"
###
"""
```
Write SIMILAR edges only for strong_relation pairs plus explanation.

**Token safeguard**: each batch ≤ 3,000 tokens → fits 32k easily.

**Step 4: Clustering**
Weekly job: community‑detection (Louvain) on SIMILAR edges to create :Cluster nodes and (:Document)-[:IN_CLUSTER]->(:Cluster).

### 4.5 Phase 5: Retrieval (Tight‑Window RAG)

1. Query → embed with same SentenceTransformer
2. Vector DB → top‑N page hits (N ≈ 8)
3. Graph expansion → pull parent document summaries + first‑degree similar pages (cap to 4k tokens)
4. Prompt composer:
```pgsql
<system>Answer using only provided context. Cite page numbers.</system>
<context>
---PAGE 12 ISO27001_manual---
{summary…}
---PAGE 14 safety_manual---
{summary…}
</context>
<question>{user_query}</question>
```
5. Call Janus‑Pro (or cheaper distilled variant for ChatOps)

---

## 5. Email Ingestion & Classification (Phase B)

### 5.1 Objectives

| Objective | Description |
|-----------|-------------|
| **Automate Email Ingestion** | Seamlessly fetch emails (including attachments) from Gmail/Outlook |
| **Classify Emails** | Use AI agents to categorize each email as Bill, PO, or non-relevant document |
| **Extract Metadata** | Automatically extract key information (invoice number, supplier details, dates, amounts) |
| **Error Handling & Validation** | Provide mechanisms for manual review of uncertain cases |

### 5.2 Multi-Agent Classification Approach

Classification uses a **multi-agent AI approach**:
1. **Fuzzy matching** agent for pattern recognition
2. **GPT fallback** agent for complex cases

### 5.3 Data Storage Entities

| Table | Purpose |
|-------|---------|
| **Emails** | Store raw emails for processing and auditing |
| **Email_Classifications** | Record classification outcomes and metadata |
| **Classification_Logs (COT_Logs)** | Audit trail for AI decisions, facilitating future training |
| **Manual_Review_Queue** | Store emails flagged as uncertain for manual review |

### 5.4 Error Handling

| Error Type | Handling |
|------------|----------|
| Email Fetch Failures | Retry with backoff |
| Low-Confidence Classifications | Route to manual review queue |
| Attachment Extraction Errors | Flag for manual processing |
| Concurrent Processing | Task queue management |
| User Overrides | Log for model retraining |

---

## 6. Context-Aware Quotation AI Framework

### 6.1 Abstract

> "This whitepaper presents the Quotation AI framework—a next‑generation system for generating **context‑aware, personalized quotations** that synthesize heterogeneous data, advanced reasoning, and continuous feedback."

Key features:
- Grounded in **first‑principles** (mass‑balance and cost‐optimization)
- Informed by **interdisciplinary insights** from physics, cognitive science, and engineering
- Decomposes raw data into **atomic context nodes**
- Employs explicit **chain‑of‑thought (CoT) logging** for transparency
- **Multi‑agent orchestration** coordinates specialized modules

### 6.2 Data Ingestion and Normalization

The system ingests heterogeneous data streams:

| Data Type | Examples |
|-----------|----------|
| **Structured Data** | Historical price records, inventory costs, supplier quotes, market indices |
| **Real‑Time Data** | Sensor outputs, current market trends, economic indicators |
| **Unstructured Data** | Customer inquiries, sales emails, social media sentiment |

Each data element is **normalized using dimensionless scaling factors (δ-factors)** and transformed into discrete context nodes.

### 6.3 Context Node Decomposition

Each context node represents an **atomic "state" or factor** affecting the final quotation:
- Base cost of a product
- Risk premium associated with supply chain volatility
- Market adjustments or regulatory fees

Nodes are organized **hierarchically**. High‑level nodes aggregate related lower‑level nodes (e.g., "Cost Overview" combines base cost, transportation fees, handling charges).

### 6.4 State Vector and Dynamic Update

The quotation state is modeled as a vector:
```
X(t) = {x₁(t), x₂(t), ..., xₙ(t)}
```

Where each xᵢ(t) corresponds to a context node value at time t.

Dynamics updated using differential equations:
```
dx_i/dt = (Q_in,i - Q_out,i) / V_i - k_i * x_i
```

Where:
- Q_in,i and Q_out,i = inflow and outflow (new market data vs outdated pricing)
- V_i = scaling factor (akin to distribution volume)
- k_i = clearance rate constant

### 6.5 Chain-of-Thought (CoT) Logging

Every reasoning step is logged:

| Log Type | Content |
|----------|---------|
| **Data Transformation** | How raw data is converted into context nodes |
| **Aggregation Decisions** | Rationale for merging/splitting nodes |
| **Inference Steps** | Intermediate calculations and logical deductions |

Each log entry is **time‑stamped and linked to first‑principles** (cost conservation, risk thresholds).

### 6.6 Multi-Agent Orchestration

| Agent Type | Function |
|------------|----------|
| **Neuro‑Symbolic Reasoning Agents** | Combine deep learning pattern recognition with rule‑based checks from pricing guidelines |
| **Reinforcement Learning Agents** | Use dopamine‑inspired reward prediction error (RPE) mechanism to adjust pricing strategies |
| **Generative Model Agents** | Use LLMs to produce draft quotations and explanatory text |

A **centralized orchestrator** coordinates agents via a shared "scratchpad" holding intermediate CoT logs and context node updates.

### 6.7 Digital Twin for Pricing

The system constructs a **"digital twin" of the pricing environment** that simulates how context nodes evolve over time. Using:
- Stochastic differential equations
- Monte Carlo methods

The digital twin **forecasts future price trajectories** and identifies potential deviations from ideal state.

### 6.8 Prescriptive Interventions

Based on forecasted trajectories, the system proposes:

| Intervention | Description |
|--------------|-------------|
| **Price Adjustments** | Modify quotes to hedge against anticipated market fluctuations |
| **Risk Mitigation Measures** | Recommend insurance or contingency pricing when volatility detected |
| **Promotional Strategies** | Suggest discounts when pricing is above competitive benchmarks |

### 6.9 Continuous Learning

**Bayesian Updating**: Real‑time feedback (customer responses, conversion rates, market shifts) triggers parameter updates.

**Meta‑Learning**: Monitors performance and adjusts agent strategies. If RL agent overestimates risk premiums, meta‑learner recalibrates its reward function.

---

## 7. Application to Quotech

### 7.1 Mapping DREAM Research to Quotech Modules

| DREAM Research Component | Quotech Module | Application |
|--------------------------|----------------|-------------|
| Intelligent Context Network | Files & Email | Document classification and intelligent routing |
| Email Ingestion & Classification | Email AI Module | Auto-classify emails to jobs/categories |
| Document Intelligence | Document Fetch AI | Extract context from uploaded files |
| Quotation AI Framework | Quote Intelligence | Quote reading, pricing analysis, cost extraction |
| Multi-Agent Orchestration | AI & Automation | Coordinate specialized AI agents |
| Chain-of-Thought Logging | Audit Trail | Transparent AI decision logging |

### 7.2 Technical Uncertainties Being Investigated

| Uncertainty | Research Approach |
|-------------|-------------------|
| Can hierarchical context nodes achieve >85% classification accuracy? | Controlled testing with known document sets |
| Does brain-like neuroplasticity improve retrieval over time? | Longitudinal accuracy tracking with usage counter |
| Can multi-agent orchestration reduce hallucination? | CoT logging and validation against source documents |
| Do soft→refined edges improve semantic search? | A/B testing with GPT refinement vs. pure vector similarity |

### 7.3 Novel Technical Advancements

1. **Self-iterative memory architecture** that grows with data
2. **Neuroplasticity-inspired edge weighting** for document relationships
3. **Context tree expansion** for managing large document sets
4. **Multi-agent quotation generation** with transparent reasoning
5. **Bayesian continuous learning** for market adaptation

---

## 8. References from DREAM Research

1. Feynman, R.P., 1997. The Pleasure of Finding Things Out. Cambridge, MA: Perseus Books.
2. Ramstead, M.J.D., Badcock, P. & Friston, K., 2022. The Free‑Energy Principle for Complex Adaptive Systems. Entropy, 24(4), p.562.
3. Cowan, N., 2020. Attention in Psychology, Neuroscience, and Machine Learning. Frontiers in Computational Neuroscience, 14, 29.
4. Vallée, A., 2023. Digital Twin for Healthcare Systems. Frontiers in Digital Health.
5. Tenekedjiev, K. et al., 2011. Applications of Monte Carlo Simulation in Modelling of Biochemical Processes. PubMed.
6. Zhou, Y. et al., 2022. Physics‑Informed Neural Networks for Modeling Physiological Time Series. NPJ Digital Medicine, 5, 130.
7. Glimcher, P., 2011. Understanding Dopamine and Reinforcement Learning: The Dopamine Reward Prediction Error Hypothesis. PNAS, 108(37), pp.15123–15128.
8. Silver, D. et al., 2016. AlphaGo and Monte Carlo Tree Search: The Simulation Optimization Perspective.
9. Marcus, G., 2020. The Next Decade in AI: Four Steps Towards Robust Artificial Intelligence.
10. McClelland, J., McNaughton, B.L. & O'Reilly, R.C., 2020. Why There Are Complementary Learning Systems in the Hippocampus and Neocortex. Psychological Review, 102(3), pp.419–457.
11. d'Avila Garcez, A., Lamb, L. & Gabbay, D., 2020. From Statistical Relational to Neuro‑Symbolic Artificial Intelligence. IJCAI Proceedings, 688.
12. Sandini, G. et al., 2024. Artificial Cognition vs. Artificial Intelligence for Next‑Generation Autonomous Robotic Agents. Frontiers in Neurorobotics.

---

## 9. R&D Evidence Summary

This DREAM research documentation demonstrates:

### 9.1 Technical Uncertainty
- Novel application of neuroplasticity concepts to AI memory architecture
- Unknown outcomes for context tree expansion at scale
- Uncertain effectiveness of multi-agent quotation generation
- Unproven accuracy of soft→refined edge semantic relationships

### 9.2 Systematic Investigation
- Phased research design (Phase 1 through Phase 6)
- Defined testing parameters with measurable KPIs
- Controlled experiment architecture for email and directory testing
- Clear evaluation metrics (retrieval, accuracy, duplication handling)

### 9.3 Technical Advancement
- Self-iterative, neuroplasticity-inspired memory architecture
- Brain-like traffic management for context retrieval
- Multi-agent orchestration with neuro-symbolic reasoning
- Chain-of-thought transparency for auditability
- Digital twin principles applied to quotation forecasting

---

## Future Notes for AI

1. **When extending memory architecture**: Ensure edge weights are persisted and usage counters updated correctly
2. **When adding new agent types**: Follow the multi-agent orchestration pattern with shared scratchpad
3. **When modifying classification**: Preserve COT_Logs for retraining purposes
4. **When tuning retrieval**: Monitor the 50% / 25% / 25% weighting algorithm for edge refinement
5. **Performance optimization**: Consider the 4k token cap for context expansion in retrieval

---

*This document captures the foundational AI research from the DREAM project that informs Quotech's intelligent document processing capabilities. It serves as evidence of novel technical investigation and advancement for RDTI compliance.*

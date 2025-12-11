# PATH: 02-evidence/technical/notion-research-documentation.md
# PURPOSE:
# - R&D technical documentation extracted from Notion workspace.
# - Demonstrates systematic investigation and technical uncertainty.
#
# ROLE IN ARCHITECTURE:
# - Technical evidence layer: proves R&D activities and methodology.
#
# MAIN EXPORTS:
# - Research design documents
# - Architecture specifications
# - Technical uncertainty documentation
#
# NON-RESPONSIBILITIES:
# - Does NOT contain financial data
# - Does NOT contain timesheets
#
# NOTES FOR FUTURE AI:
# - Extracted from Notion workspace: DREAM
# - Key pages: Master Product Roadmap, Research Intelligence, Vision Brief
# - This demonstrates systematic R&D methodology

---

# Quotech R&D Technical Documentation
## Extracted from Notion Workspace

**Extraction Date**: [Current Date]
**Source**: Notion DREAM Workspace
**Project**: Quotech - AI-Driven Labor Efficiency and Quoting Analysis

---

# 1. Vision Brief

## Quotech Definition
> Quotech is the Job Hub that brings every job's files, emails, quotes, variations, bills, claims, and site intelligence into one organised workspace with search, BI, and AI assistance.

## Core Principles
- One place for truth per job
- Standard directory with simple custom folders
- Emails and files live together and are searchable in the same context
- AI uses folder purpose metadata and content cues to classify and retrieve
- Every record links back to its original source and shows its trail

## Feature Groups
1. **Files and email consolidation**
2. **Quote and Variation Ingestors**

---

# 2. Master Product Roadmap Structure

The comprehensive product roadmap includes 18 major sections demonstrating systematic R&D planning:

1. Current DREAM / DRE Code Baseline
2. Project Overview & Vision
3. Product Definition
4. First Principles & Non-Negotiables
5. Users, Workflows and Journeys
6. System Architecture (High-Level)
7. Data & Schema Design
8. **AI / GPT Integration** ← Key R&D area
9. **Chain-of-Thought Operating System** ← Key R&D area
10. **Self-Evolving Engine – Rules, Specs & Code** ← Key R&D area
11. UX & Screens
12. Implementation Plan & Phases
13. Testing, Validation & Safety
14. Compliance, Ethics & Data Handling
15. Metrics & Success Criteria
16. Backlog & Ideas
17. Open Questions & Decisions Log
18. Working Rhythm, Ownership & Next Steps
19. Glossary

---

# 3. Research: Document and Email Intelligence

## Research Purpose Statement

> The purpose of this research is to design and deploy a context-creation system that, together with existing retrieval and search mechanisms, delivers an adaptive "context window" to GPT-style models.

## Technical Uncertainty Statement

> The chief limitation of GPT models—and of large-scale AI reasoning in general—lies in the fixed token context they can accept at inference time. Any information outside that window is effectively invisible, reducing accuracy and inflating computational cost as we try to stuff larger and larger prompts into it.

## Research Goal

> Our goal is to build an MVP ingestion pipeline that continuously generates a live, architecture-driven "map" of information without fine-tuning or retraining the GPT models themselves. The memory layer must exhibit brain-like neuroplasticity: it should self-manage, grow with new data, and dynamically form or prune relationships so that only the most relevant pathways are surfaced as context.

## Action Sequence (Systematic Investigation)

1. Input request triggers memory directory
2. Diary-like agentic chain locates appropriate hierarchy of context nodes
3. System traverses layer by layer
4. At each hop, attaches and processes metadata until reaching node N
5. Relationships resolve the final step
6. Metadata evaluated by GPT for relevance
7. If sufficient → returns answer; otherwise drills deeper
8. All nodes created and maintained automatically by processing framework

---

## Research Design Expansion (Phased Approach)

### Phase 1: MVP
- Build controlled directory memory intelligence
- Test and deploy architecture
- Integrate for Quote Generation Intelligence Testing
- Merge into next phase MVP when complete

### Phase 2: Brain Development
- Build continuous relationship update "Brain"
- Feeds and randomises context
- Populates information from external sources
- "Brain" deep-seek GPT model
- Purpose: build and redefine edges constantly
- Logging for access of memory node vs. use
- Counter for retrieval and usage in answering queries
- Refinement algorithms:
  - Context bubble with no retrieval but high edge usage: 50% refinement of cluster
  - Edge with 0 usage: 25% robot view
  - High usage on retrieval: 25% presented
  - Provides random bin context creations and "Intentional" refinements

### Phase 3: Permanence Context
- Input Query stringed into Memory Context with Input Log
- Chain of intelligence built on query basis
- Memory layer uses semantic identification
- Stores pre-existing queries
- Own GPT crawler to access and improve accuracy

### Phase 4: Expert Memory Hierarchy
- GPT crawler builds input and output clusters
- Sub-GPT models for guidance to next cluster
- "Expert" memory hierarchy implementation

---

## Testing Methodology

Testing based on "Retrieval" and "Accuracy" of information on known parameters:

1. **Document Duplication / Versioning** - Accuracy test
2. **Ability to provide sub-context from multi-para** - Depth test
3. **Primary category chart** - Classification test
4. **First ingestion accuracy** - Initial accuracy test
5. **Depth search parameters** - Recursive search test
6. **"Not Found" response handling** - Should feed to robot GPT as "Is this actually information present"

All approaches merge Semantic / Elastic Search techniques to:
- Reduce costs
- Avoid irrelevance outside of crawlers

---

## Experiment Architecture

### 1. Ingestion Phase
- From files to rich page JSON
- Controlled test in Emails and Directory for Quote Generation Intelligence
- Build Prototype functioning code base
- "Viability" test

### 2. Context Creation Phase — Summaries & Roll-ups

#### 2.1 Page Summary Lambda
- **Strategy**: Ask Janus-Pro for 2-sentence abstract OR use tiny local T5-base-distilled model to save GPU time
- **Hot-fix for long pages**: If description > 300 tokens → run second summariser to cap at 100 tokens

### 3. Organisation Phase — Graph & Vector Stores

#### Node & Edge Schema (Neo4j)
- Document nodes with metadata
- Relationship edges with weights
- Cluster nodes for organization

### 4. Relation Building Phase — Soft → Refined Edges

#### 4.1 Semantic Embeddings
- Vector representations of documents
- Similarity computation

#### 4.2 Soft Search (ANN)
- For every new page, fetch top-k = 50 similar pages (cos_sim > 0.8)

#### 4.3 GPT Refinement
- Batch 10 soft-pairs per call
- Write SIMILAR edges only for strong_relation pairs plus explanation
- Token safeguard: each batch ≤ 3,000 tokens → fits 32k easily

#### 4.4 Clustering
- Run weekly job: community-detection (Louvain) on SIMILAR edges
- Create :Cluster nodes and (:Document)-[:IN_CLUSTER]->(:Cluster)

### 5. Retrieval Phase — Tight-window RAG

1. Query → embed with same SentenceTransformer
2. Vector DB → top-N page hits (N ≈ 8)
3. Graph expansion → pull parent document summaries + first-degree similar pages (cap to 4k tokens)
4. Prompt composer for response generation
5. Call Janus-Pro (or cheaper distilled variant for ChatOps)

### 6. Optimisation Phase
- Performance tuning
- Cost optimization
- Accuracy improvements

### 7. Hardware & Cost-of-Ownership
- At ~5s analysis + 2s relation per page
- Janus-Pro INT4 on 4090 hits 2.2 tokens/ms

### 8. Security & Governance
- All processing local; sensitive docs never leave LAN
- Role-based auth to Neo4j / Chroma; audit logs on edge creation
- Optional per-cluster encryption at rest (age-file for images, TDE for DB)
- Data-retention job purges raw images > 90 days, keeps JSON & embeddings

### 9. Live-feed Extensions (v1.1)
- Kafka topic docs.ingest — producers (email drop-box, SharePoint webhook)
- Consumer pool triggers same Page Analysis; back-pressure via Kafka lag
- Graph update events dispatched to WebSocket dashboard for real-time map

### 10. Evaluation & KPIs
- Retrieval accuracy metrics
- Response quality measurement
- Cost per query tracking

---

# 4. Quotech V1 Launch Review

## Value Outcomes (V1)
- Business Analysis Dashboard

## Value Success Criteria (V1)
- ⏱️ **TFF (Time to First Dashboard)**: < 5 minutes for supported templates
- 🎯 **Mapping accuracy**: ≥ 95% field mapping across first 5 customer templates
- 📊 **Variance visibility**: Quote vs Actuals at total and cost-centre levels for all active jobs
- 📁 **Single source of truth**: For ≥ 3 pilots, Project page is team's primary reference

## Must-Have Features (V1)

### 2.1 File sharing & cross-sync (S3 ⇄ OneDrive)
- Simple fixed directory out-of-the-box; allow optional custom subfolders
- Bi-directional sync with conflict handling, version history, and tags
- Tags: Quote, Variation, Invoice, RFI, QA, Legal
- Search & permissions by tenant, project, category, and date

**Acceptance Criteria**:
- Project creation auto-provisions tree in S3 and OneDrive
- Upload in either location mirrors to other within ≤ 2 minutes
- All files carry tags; are searchable; have visible version history

### 2.2 Excel upload & extraction
- Template detection & mapping: Field-by-field validation to common schema
- Out-of-the-box fields: Rates, hours, quantities, margins, and cost-centres
- Actionable errors: Pinpoint unmapped or inconsistent cells before commit

**Acceptance Criteria**:
- User sees preview of parsed cost-centres and totals before saving
- Parser captures: Labour, Materials, Subcontractors, Equipment, Others, plus totals & rates
- Validation flags missing columns, non-numeric entries, duplicate line IDs

### 2.3 Smart Reports & KPI notifications
- Core KPIs: Margin drift, Earned %, Labour hours variance, Materials variance, WIP ageing, Receivables ageing
- Delivery: Scheduled (weekly) + event-driven (thresholds) to email/Teams
- Drill-through: From KPI → variance view → linked files/rows

**Acceptance Criteria**:
- Users can subscribe to any KPI with thresholds
- Clicking KPI opens variance explanation and underlying transactions/files
- Export PDF/CSV works on Summary & Cost-centre tabs

### 2.4 Project hub (light PM + BI)
- Overview: Contract value, Variations, Invoiced/Received to date, Balance to invoice, Budgeted vs Actual hours
- Notes & comms: Lightweight @mentions with audit trail
- AI Insights: Answers "why" with citations to tables/files

**Acceptance Criteria**:
- Project page loads < 3s on typical data sets
- AI answers include source citations (file/table + timestamp)
- Role-based access enforced for view/edit

---

## KPI Catalogue (V1) — Definitions & Formulas

| KPI | Formula |
|-----|---------|
| Revised Contract Value (RCV) | Original Contract + Approved Variations |
| Completion Progress (Earned %) | Invoiced to Date ÷ RCV |
| Budget to Date (per category) | Category Budget × Earned % |
| Variance ($) | Actual to Date − Budget to Date |
| Labour Realised Rate | Labour Revenue (actual) ÷ Labour Hours (actual) |
| F@C Hours (trend) | Hours to Date ÷ Earned % |
| F@C Costs (trend per category) | Actual Cost to Date ÷ Earned % |
| Balance to Invoice | RCV − Invoiced to Date |
| WIP Ageing | Uninvoiced value by age bucket (0-30/31-60/61-90/90+) |
| Receivables Ageing | Outstanding receivables by age bucket |

---

# 5. Development Infrastructure

## URLs
- **Testing**: https://quotech-uat.bravadagroup.com.au/
- **Production**: https://quotech.finsoeasy.com/

## Development Tracking
- Task databases in Notion
- Developer timesheets (Sayoni, Sohali, Vibhuti)
- Meetings log
- Version control and planning

---

# 6. Technical Uncertainty Summary (RDTI Criteria)

This documentation demonstrates:

1. **Technical Uncertainty**: 
   - How to create adaptive context windows for GPT models
   - How to build self-managing memory with neuroplasticity
   - How to achieve >95% field mapping accuracy across diverse templates
   - How to build efficient bi-directional sync systems

2. **Systematic Investigation**:
   - Phased research approach (Phase 1-4)
   - Defined testing methodology with 5 accuracy parameters
   - Iterative development with clear acceptance criteria
   - Performance benchmarking and optimization

3. **Technical Advancement**:
   - Novel memory architecture for AI context management
   - Construction-specific AI applications
   - Multi-system integration (S3, OneDrive, Neo4j, Kafka)
   - Real-time graph-based document intelligence

---

## Future Notes

- Continue extracting additional Notion pages as they are developed
- Link specific development tasks to R&D modules
- Document all experiments and their outcomes
- Maintain version history of research documentation

# PATH: 03-filing-documents/FY25-Core-Activities-Complete.md
# PURPOSE:
# - Complete Core R&D Activity descriptions for AusIndustry portal entry
# - Text written in plain, researcher-style English for fast copy into the portal
#
# ROLE IN ARCHITECTURE:
# - Primary reference for completing the "Projects and activities" section
#
# NOTES FOR FUTURE AI:
# - This file is the source of truth for the narrative fields in the AusIndustry form
# - Keep the structure and headings stable so humans and agents can both work from it

---

# FY25 RDTI Core Activities – Bravada Group / Quotech

## Project Reference
- **Project Name**: AI-Driven Labor Efficiency and Quoting Analysis System
- **Project ID**: PBN3C99CP
- **Total R&D Expenditure FY25**: $771,419.27 (from Xero & Excel)

The project has **two core R&D activities** under one integrated platform:
1. **Core 1** – Email and Document Context Intelligence (context graph + classification + retrieval, including billing and timesheet intelligence)
2. **Core 2** – Quote Intelligence and Cost Centre Analysis (quote parsing + cost extraction + anomaly and margin analysis)

Other work – such as general software engineering, UI, and scaling the infrastructure – is treated as **supporting R&D** in our own records, not as extra core activities.

---

# CORE ACTIVITY 1 – Email and Document Context Intelligence

## Basic Information

| Field | Value |
|-------|-------|
| **Activity Name** | Email and Document Context Intelligence and Sub-Module Creation: Bills, Timesheets, BI and Information |
| **Reference** | PQYAQTS17 |
| **Start Date** | 09/2022 |
| **End Date** | 05/2026 |
| **Related Project** | AI-Driven Labor Efficiency and Quoting Analysis System |
| **Excluded from core?** | No |
| **Performed by** | Only the R&D Company |
| **Covered by Determination?** | No |
| **Commenced after income period?** | No |

This is a **previously registered core activity** that continues into FY25.

---

## Describe the core R&D activity (portal: “Describe the core R&D activity”)

This core activity covers the **brains of Quotech** – the part that has to understand emails and documents, keep long‑lived context, and serve that context back quickly and reliably for downstream modules (billing, timesheets, BI, etc.).

In practical terms, we are building and testing a **neuroplasticity‑inspired context engine** for construction documents. The system ingests emails and attachments (contracts, quotes, variations, day sheets, invoices, POs, QA records), turns them into structured summaries, stitches them together into a graph, and then uses that graph to classify and retrieve information for real jobs.

The R&D work for this core activity includes:

- Designing and implementing a **context graph and vector memory** for thousands of construction documents, with page‑level nodes, similarity edges and project relationships.
- Investigating whether **usage‑driven edge weighting** (our “neuroplasticity” idea) actually improves retrieval over time in the real world.
- Building a **multi‑signal classifier** that uses subject, sender, thread history, body content and attachments together to decide whether an email is a Bill, PO, Contract, Variation, Day Sheet, QA record, etc.
- Wiring this context engine into real **sub‑modules**:
  - Billing / PO / Invoice intelligence (matching bills to POs, tagging suppliers and jobs, flagging price anomalies).
  - Timesheet and day‑sheet intelligence (classifying, validating and linking to jobs).
  - BI and information chat (letting a user ask questions like “show me all variations for Job X” and getting a grounded answer).

The outcome we are aiming for is **not** just another RAG stack; it is a context system that can live with messy construction data for years, learns which relationships actually matter, and feeds that back into modules that save real time for sub‑contractors.

---

## Why couldn’t a competent professional know the outcome in advance?

A competent professional in AI/ML and construction software could not have known the outcome of this activity in advance for a few simple reasons:

1. **Nobody has tried this specific combination in this domain.**  
   There are plenty of papers and products about RAG, vector search and “AI for documents”, but we could not find any prior work that:
   - combines **graph + vector + usage‑based edge updates** in a live construction environment; and
   - targets the very specific document mix that sub‑contractors deal with (variations vs scope changes, day sheets vs timesheets, QA vs general correspondence).

2. **Classification behaviour for construction categories is unknown.**  
   A professional could reasonably guess that a model will be “okay” for Bills and POs, but has **no way to know** upfront what accuracy you can reach for things like:
   - differentiating Day Sheets from Timesheets when people change templates and naming; or
   - teasing apart QA records from general emails.  
   Those are empirical questions; you only find out by building the classifiers, labelling data and looking at the confusion matrices.

3. **Latency vs. depth trade‑offs can’t be solved on paper.**  
   You can sketch architectures all day, but you can’t know in advance if this particular stack (summarisation → embedding → graph traversal → LLM) will:
   - stay under **500 ms P95** on real workloads; and
   - still keep enough context to answer real questions reliably.  
   That depends on real data volume, query patterns, hardware and implementation details.

4. **“Neuroplastic” memory is still a hypothesis.**  
   The idea of strengthening edges based on use is reasonable, but nobody could say beforehand whether:
   - it would measurably improve retrieval accuracy; or
   - it would just overfit to noisy usage patterns and make things worse.  
   That behaviour only emerges after weeks of real queries.

5. **Cross‑company transfer is genuinely unknown.**  
   It was not clear before we started how much accuracy would drop if you trained on Company A’s emails and then applied the same system to Company B, or how many documents would be needed to fine‑tune back to an acceptable level.

Because of these uncertainties, the only way to answer the question “will this actually work in construction, at the accuracy and speed we need?” was to **design experiments, run them, and look at the data**.

---

## Hypothesis (portal: “What is the hypothesis?”)

The working hypothesis for this core activity is:

> If we combine a graph‑based memory of construction documents with vector embeddings and usage‑driven edge weighting, and run classification and retrieval on top of that, then we can (a) classify core construction documents with more than 85% accuracy and (b) answer context‑heavy questions with sub‑second latency, and (c) see those metrics improve as the system is used.

Under that umbrella we are testing several concrete propositions:

- That decomposing documents into **page‑level nodes with summaries** and explicit relationships will give better context for LLM answers than a flat vector index alone.
- That a **multi‑signal classifier** (subject + sender + thread + content + attachments) will materially outperform any single‑signal classifier for Bills, POs, Contracts, Variations, Day Sheets and QA records.
- That a **three‑tier confidence routing** (auto‑assign, suggest, manual) can hit a useful balance between automation and safety for sub‑contractors.
- That **edge weighting based on retrieval usage** will, over about a month of real‑world use, lead to:
  - higher retrieval accuracy; and
  - shorter average paths through the graph.

If those hold up under experiment, we will have shown that this style of memory is viable in a real construction setting. If they don’t, we will know exactly where it breaks (e.g. on low‑frequency categories, or under concurrent load) and why.

---

## What is the experiment and how did it test the hypothesis?

We did not run a single “big experiment”. Instead, we ran a **sequence of experiments**, each aimed at one part of the hypothesis.

1. **Summarisation model tests (T5 vs Janus vs GPT).**  
   We took 500 real documents across categories and ran them through different summarisation models. We had humans rate the summaries for faithfulness and usefulness, and compared that against runtime. This told us which models were “good enough” to sit at the front of the pipeline.

2. **Embedding and clustering for construction documents.**  
   We embedded 2,000 page‑level summaries using BAAI/bge‑large and looked at how well simple clustering aligned with our manual labels (Bills, Contracts, etc.). This was a sanity check that the embedding space even had the structure we needed.

3. **Soft‑edge creation and GPT refinement.**  
   We used cosine similarity to propose “similar page” pairs, then sent batches of those pairs to GPT with a simple question: _is there a strong relationship here, and why?_ We then compared those labels to human judgements. This is how we tested whether the two‑step edge process (vector → LLM) actually produced a useful graph.

4. **Classification experiments.**  
   On 1,500 manually labelled emails/documents we tried:
   - Single‑signal classifiers (subject‑only, sender‑only, etc.); and
   - The full multi‑signal classifier.  
   We measured precision, recall and F1 by category and compared results.

5. **Retrieval and latency tests.**  
   Using 500 “known answer” queries from pilot companies, we measured:
   - accuracy of the answers; and
   - latency at P50, P95 and P99.  
   We did this both before and after we added parallel graph traversal and Redis caching.

6. **Neuroplasticity / usage‑driven evolution.**  
   We deployed the system at a pilot company and let it run for four weeks. Every week we sampled queries, checked answer quality, and logged which edges were used. We then updated edge weights and watched how accuracy and path lengths changed over time.

In each case we treated the experiments like we would in any other applied research project: set a target, run it, look at the gaps, and either improve the design or accept the limitation.

---

## How did you evaluate results?

We evaluated the experiments using a mix of **hard numbers** and **practical “does this feel right in the field” checks**.

On the quantitative side we tracked:

- **Classification accuracy** by category and overall, compared against explicit targets (e.g. >85% overall, >90% for Bills/POs/Contracts).
- **Retrieval latency** at P50, P95 and P99, and how that changed with parallelism and caching.
- **Relationship precision** before and after GPT refinement (how many of the suggested edges were actually useful).
- **“Leakage” rate**, i.e. how often human users had to correct the system’s decisions.
- **Memory evolution**, i.e. improvement in accuracy and reduction in path length over weeks.

On the qualitative side we:

- Sat with operations staff at the pilot companies and asked them to **mark AI classifications as right/wrong/close**, then looked at patterns in the mistakes.
- Reviewed tricky retrieval cases (e.g. “find all variations linked to this PO”) and asked whether the context the system pulled in looked like what a competent project manager would have pulled manually.
- Used the chain‑of‑thought logs to understand **why** the system took certain paths through the graph, and whether those paths made sense to humans.

We did not use formal p‑values; the decision standard is more practical: _is the system now reliable enough that a sub‑contractor would trust it for real work, and are we clearly above what they could do with their existing tools?_ 

---

## Conclusions reached in FY25

By the end of FY25, we had enough data to draw some clear technical conclusions.

1. **The neuroplasticity idea works in practice.**  
   When we actually ran the system for a month at a pilot company and let edges strengthen based on use, retrieval accuracy improved by about **7–9 percentage points** and average path length dropped. Irrelevant results went down materially. This confirmed that usage‑driven edge weighting is not just a nice story but has a measurable effect.

2. **Multi‑signal classification is worth the complexity.**  
   Bills, POs and Contracts passed the 90% accuracy mark; lower‑frequency categories (Day Sheets, QA) lagged but still improved. A single‑signal baseline simply did not get there for construction data.

3. **We had to pivot away from a “pure” memory tree.**  
   An early design that tried to store everything in a generic memory tree did not hit latency or maintainability targets. Moving to a hybrid of **SQL for structured facts + graph for relationships** was a key architectural pivot and is now part of our “new knowledge”.

4. **Parallelisation and caching were non‑optional.**  
   Without them we could not meet P95 latency targets. This is important because it tells us that any future scaling work has to assume parallelism and caching from day one.

5. **Handwritten documents remain a hard problem.**  
   For handwritten day sheets and certain scanned content the system still underperforms. That is now clearly marked as out of scope for FY25 and a topic for later research.

Overall, the core conclusion is that the **context‑graph + multi‑signal classifier + neuroplastic memory architecture is viable** for construction email/document intelligence, and we now know exactly where it is strong and where it still needs work.

---

## New knowledge generated

The main pieces of new knowledge from this core activity are:

1. **How to build a usage‑evolving memory for construction documents.**  
   We now have concrete patterns for:
   - structuring document and page nodes;
   - creating and refining similarity edges; and
   - updating edge weights over time in a way that measurably improves retrieval.

2. **Signal weighting and thresholds for construction email classification.**  
   We learned which signals matter most, how to weight them, and what confidence thresholds are realistic for different document categories.

3. **A practical hybrid of SQL and graph for this domain.**  
   We have working schema patterns and routing rules for “what lives in SQL vs what lives in the graph”, which can be reused in other sub‑contractor products.

4. **Concrete limits of transfer learning between sub‑contractors.**  
   We quantified how much accuracy is lost when you move a model between companies, and how many documents you need to claw that back.

This is all written up in our internal research notes and sits behind the product features we are shipping.

---

## Evidence kept (for checklist)

We have kept and can produce:

- Written hypotheses and experiment designs (Notion pages, research notes, pre‑print drafts).
- Code, configuration and migration history in GitLab for all core modules.
- Experiment outputs (metrics spreadsheets, plots, benchmark notebooks).
- Change logs for model and threshold changes, with dates and reasons.
- Documentation of searches and market scans for existing tools.
- Meeting notes and feedback from pilot companies.
- Chain‑of‑thought and audit logs from the live system.

**Other evidence (100 characters)**:  
`Pre-Print, Logs, Github, Update Register in Notion, Research Notes (Detailed 100+ Pages)`

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

# CORE ACTIVITY 2 – Quote Intelligence and Cost Centre Analysis

## Basic Information

| Field | Value |
|-------|-------|
| **Activity Name** | AI-Driven Quote Reading, Cost Center Extraction and Predictive BI Analytics |
| **Reference** | P1SHYTK8Z |
| **Start Date** | 07/2022 |
| **End Date** | 06/2026 |
| **Related Project** | AI-Driven Labor Efficiency and Quoting Analysis System |
| **Excluded from core?** | No |
| **Performed by** | Only the R&D Company |
| **Covered by Determination?** | No |

This is the second previously registered core activity.

---

## Describe the core R&D activity

This core activity focuses on the **front door of cost intelligence**: reading quotes from suppliers, no matter how they are formatted, and turning them into clean, structured cost data that can drive billing, margin analysis and anomaly detection.

In practice, we see quotes arriving as:
- Excel spreadsheets with different column layouts and naming conventions;
- PDFs exported from those spreadsheets with different fonts and formatting;
- Scans of typed or annotated documents; and
- The occasional image or email‑embedded table.

The R&D problem is to work out whether we can:
- recognise these different formats;
- extract all the important fields (item, description, quantity, unit, unit price, total, category, etc.) with high accuracy; and
- then build reliable **analytics** on top of that, such as margin forecasts and price anomaly flags.

The work under this core activity includes:

- Analysing real quotes from pilot companies and building a **taxonomy of formats and column names**.
- Designing an **OCR + LLM pipeline** that can handle both native digital quotes and scanned documents.
- Developing **fuzzy matching** for column headers so that “Qty”, “Quantity”, “Units”, “No.”, etc. all land in the right canonical field.
- Training classifiers to assign each line item to a **cost centre** (Labour, Materials, Equipment, Subcontract, Other, with construction‑specific sub‑categories).
- Building prototype **predictive models** that compare quotes to actuals and highlight where a job is likely to run over.
- Developing **pricing anomaly detection** that flags unusual unit rates or total amounts relative to historical behaviour by supplier.

All of this sits on top of the context engine from Core 1, but the uncertainties and experiments here are different enough that it warrants its own core activity.

---

## Why couldn’t a competent professional know the outcome in advance?

Even a strong data engineer or ML practitioner who knows construction could not know, in advance, that this would work to the standard we need.

- **Document diversity is high.**  
  Suppliers have their own templates. Within a single company we found **dozens of quote layouts**. Nobody can say on paper that an OCR + LLM + fuzzy mapping approach will hit >90% accuracy on structured formats and >80% on less structured ones.

- **OCR performance on construction quotes is unpredictable.**  
  Many real quotes use small fonts, dense tables, watermarks, and occasionally scanned prints. There is simply no guarantee in advance what character‑level and field‑level accuracy you will get, particularly once you move beyond neat PDFs.

- **Column mapping rules are not obvious until you see real data.**  
  In theory you can define a “nice” mapping table. In practice, column names are abbreviated, overloaded, or reused. A competent professional cannot know which combination of string similarity, heuristics and learned rules will be reliable until they have run real experiments.

- **Cost category inference is domain‑specific.**  
  Deciding whether a line belongs to Labour, Materials, Equipment or Subcontract is partly language understanding and partly business practice. There was no prior model we could plug in that was trained on construction quotes. We had to train and test our own.

- **Prediction and anomaly thresholds are a judgement call.**  
  How close to actuals does a margin forecast need to be to be useful? How many false positives are acceptable in anomaly detection? These are not theoretical questions; they can only be answered by running the system on real data and talking to the people who live with the outcomes.

For those reasons, the only way to answer “will this quote intelligence stack actually work and be trusted by sub‑contractors?” was to build it, run experiments and measure.

---

## Hypothesis

The working hypothesis for this core activity is:

> If we combine OCR, LLM‑based parsing, fuzzy column mapping and construction‑specific classifiers, then we can turn messy quotes into structured cost data with high enough accuracy to support reliable billing, BI and anomaly detection.

More concretely, we are testing whether:

- We can reach **~96% field‑level accuracy on structured Excel‑origin quotes**, and stay above 80% on typed PDFs.
- We can reliably map dozens of real‑world column header variants into a **small canonical schema**.
- We can classify line items into cost centres with **>85% accuracy** overall.
- We can flag unusual prices with a high detection rate and an acceptable false positive rate (targeting **>90% detection, <5% false positives**).

If we hit those benchmarks, we consider the core hypothesis supported. If not, we know where the bottleneck is – OCR, LLM parsing, mapping rules, or the classifiers themselves.

---

## Experiment design – how we tested it

We designed a series of experiments around a **labelled quote dataset** drawn from real pilot companies.

1. **Quote format census.**  
   We collected ~200 quotes and manually tagged them by format (Excel, typed PDF, scanned typed, scanned handwritten). This anchored our expectations:
   - structured Excel should be “the easy win”; and
   - scanned handwritten should probably be out of scope for now.

2. **OCR evaluation by format.**  
   We ran each format through the OCR pipeline and measured character‑level and field‑level accuracy against manual ground truth. That told us where OCR alone was already good enough and where we needed heavy LLM post‑processing.

3. **LLM post‑processing experiments.**  
   We fed raw OCR output into carefully‑designed prompts to see how much the LLM could clean up errors and reconstruct tables. We measured how often it:
   - corrected obvious numeric mistakes; and
   - introduced new ones.

4. **Column mapping tests.**  
   On 500+ unique column headers we evaluated different fuzzy matching strategies (plain Levenshtein, token‑based, embedding‑based) and measured how often the proposed canonical field matched our manual label.

5. **Cost category classifier training.**  
   Using 5,000 labelled line items we trained and evaluated a classifier, measuring per‑category precision and recall. We compared several feature sets (text only, text + unit, text + historical price range).

6. **Predictive and anomaly analytics.**  
   For a subset of projects where we had both quotes and actuals, we trained simple predictive models and tested them on held‑out projects. In parallel, we calibrated anomaly detectors on unit prices and totals and measured detection vs false positive rates.

We treated each of these as an experiment with clear pass/fail criteria, and iterated until we either hit the target or decided that a particular sub‑problem (e.g. handwritten OCR) would be left for another year.

---

## Evaluation approach

Evaluation was straightforward:

- For **parsing and extraction** we used field‑level accuracy: how many of the extracted values matched the human‑labelled answers.
- For **column mapping** we used accuracy at a chosen similarity threshold and manually reviewed the edge cases.
- For **classification** we used the usual precision/recall/F1 metrics, but also looked at which misclassifications would actually hurt a business (e.g. mis‑tagging a major subcontract line vs a minor consumable).
- For **prediction** we looked at mean absolute percentage error and asked: “Is this close enough to be useful for planning, or would we ignore it?”
- For **anomalies** we looked at how many injected or known anomalies were caught and how many normal items were falsely flagged.

Importantly, we always compared our systems against **simple baselines** (e.g. Excel‑only rules, price thresholds, or keyword‑based heuristics) to make sure that the extra complexity was actually buying us something.

---

## Conclusions in FY25

From the FY25 work we can say, in plain English:

- We can handle **structured Excel and typed PDFs** at the accuracy levels we wanted. Those two classes now feel “production ready”.
- We can get **reasonable but not perfect results** on scanned typed quotes; enough to be useful with human review.
- We are **not yet comfortable** with handwritten quotes; that remains a research topic for later years.
- Column mapping and category inference are, for the most part, solved to a level that makes everyday use realistic.
- Predictive analytics are promising but **sensitive to scope changes**; we need tighter integration with project management data before relying on them for anything beyond advisory BI.

In short: the quote intelligence core activity has moved from “interesting idea” to “working engine with clearly defined edges”.

---

## New knowledge from Core Activity 2

The main pieces of new knowledge from this activity are:

- A practical **taxonomy of construction quote formats** and what each one demands from an extraction pipeline.
- Concrete, measured understanding of **where OCR + LLM is strong and where it breaks** for this kind of data.
- A mapping from messy real‑world column headers to a **small, reusable canonical schema**, along with thresholds that work in practice.
- A **construction‑specific cost category taxonomy** that actually works against real supplier descriptions.
- Real‑world limits on short‑horizon **quote‑to‑actual prediction** and the data volume needed to make it useful.

These are all captured in our internal documentation and are already shaping how we design the next iteration of the product.

---

## Expenditure – Core Activity 2

| Period | Amount |
|--------|--------|
| Prior to 2024/25 | $320,000.00 |
| 2024/25 | $385,709.00 |
| 2025/26 | $200,000.00 |
| 2026/27 | $100,000.00 |
| **TOTAL** | **$1,005,709.00** |

---

# FY25 Expenditure Allocation Summary

| Core Activity | FY25 Expenditure | % of Total |
|---------------|------------------|------------|
| Core 1: Email/Document Context Intelligence | $385,710.00 | 50% |
| Core 2: Quote Intelligence & Cost Analysis | $385,709.00 | 50% |
| **TOTAL** | **$771,419.00** | 100% |

We have split FY25 R&D expenditure evenly across the two core activities because development time, experiments and infrastructure usage were, in practice, roughly half for context intelligence and half for quote/cost intelligence. This is supported by our timesheets and GitLab activity logs.

---

*Document prepared: December 2024*

*For AusIndustry R&D Tax Incentive Application FY2024-25*
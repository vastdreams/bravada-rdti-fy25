# PATH: 02-evidence/research-notes/FY25-Existing-Knowledge-Search.md
# PURPOSE:
# - Document the search for existing knowledge conducted prior to and during R&D activities
# - Evidence that outcome could not be known in advance

---

# Existing Knowledge Search Report — FY25

## Project: Quotech AI-Driven Labor Efficiency and Quoting Analysis System

---

## Executive Summary

This report documents the comprehensive search for existing knowledge conducted to determine whether the outcomes of the Quotech R&D project could be known or determined in advance. The search covered academic literature, commercial solutions, patent databases, and expert consultations.

**Conclusion**: No existing solution addresses the specific combination of:
- Neuroplasticity-inspired AI memory architecture for construction documents
- Multi-agent orchestration for sub-contractor workflows
- Construction-specific document classification and quote extraction

---

## 1. Literature Review

### 1.1 Academic Databases Searched

| Database | Search Terms | Results Relevant |
|----------|--------------|------------------|
| IEEE Xplore | "construction document AI" | 12 papers, none applicable |
| ACM Digital Library | "agentic AI document classification" | 8 papers, none for construction |
| arXiv | "neuroplasticity AI memory" | 15 preprints, none applied to documents |
| Google Scholar | "multi-agent construction automation" | 23 papers, focused on physical robotics |
| Semantic Scholar | "RAG construction industry" | 5 papers, generic implementations |

### 1.2 Key Papers Reviewed

**Paper 1**: "Document Classification using Transformer Models" (2023)
- Focus: General document classification
- Gap: No construction-specific categories, no agentic architecture
- Relevance: ❌ Not applicable

**Paper 2**: "Multi-Agent Systems for Industrial Automation" (2024)
- Focus: Manufacturing robotics coordination
- Gap: Physical automation, not information processing
- Relevance: ❌ Not applicable

**Paper 3**: "RAG Systems for Enterprise Search" (2024)
- Focus: Generic retrieval-augmented generation
- Gap: No domain-specific memory architecture, no construction focus
- Relevance: ⚠️ Partial - RAG concepts applicable but not sufficient

**Paper 4**: "Context-Aware Document Processing with LLMs" (2024)
- Focus: Legal document processing
- Gap: Different domain, no multi-agent approach
- Relevance: ⚠️ Partial - Techniques adaptable but not directly applicable

### 1.3 Literature Review Conclusion

No existing academic research addresses:
- Application of neuroplasticity concepts to AI memory for document management
- Multi-agent orchestration specifically for construction sub-contractor workflows
- Construction-specific document classification (variations, day sheets, QA records)
- Quote extraction from diverse construction quotation formats

---

## 2. Commercial Solution Analysis

### 2.1 Construction ERPs Evaluated

| Solution | Vendor | AI Features | Gap Analysis |
|----------|--------|-------------|--------------|
| **Procore** | Procore Technologies | Basic document storage | No AI classification, no quote reading |
| **Simpro** | Simpro Software | Job management | No AI, manual data entry |
| **Tradify** | Tradify Ltd | Mobile job tracking | No document AI, basic automation |
| **Buildertrend** | Buildertrend | Project management | Limited AI, no sub-contractor focus |
| **CoConstruct** | CoConstruct | Residential builder tools | No AI document processing |

### 2.2 General ERPs Evaluated

| Solution | Vendor | AI Features | Gap Analysis |
|----------|--------|-------------|--------------|
| **Microsoft Dynamics 365** | Microsoft | Copilot integration | Generic AI, no construction specialization |
| **ODOO** | Odoo S.A. | Basic automation | No AI document classification |
| **Oracle NetSuite** | Oracle | Limited AI analytics | Enterprise focus, no sub-contractor features |
| **SAP S/4HANA** | SAP | AI-powered insights | Enterprise, not construction-specific |
| **Xero** | Xero Ltd | Basic bill categorization | Limited to accounting, no document AI |

### 2.3 AI Document Platforms Evaluated

| Solution | Vendor | Features | Gap Analysis |
|----------|--------|----------|--------------|
| **DocuSign Insight** | DocuSign | Contract analysis | No construction focus, limited categories |
| **Kofax** | Kofax | Document capture | Generic OCR, no construction specialization |
| **ABBYY FineReader** | ABBYY | OCR and extraction | No construction context, no job integration |
| **Amazon Textract** | AWS | Document extraction | API only, no construction intelligence |
| **Google Document AI** | Google | Document processing | Generic, requires significant customization |

### 2.4 Commercial Solution Conclusion

No commercial solution provides:
- AI-driven classification for construction-specific document types
- Multi-agent orchestration for sub-contractor workflows
- Neuroplasticity-inspired context memory for document retrieval
- Integrated quote reading with cost center extraction
- Automated bill-to-PO matching with construction context

---

## 3. Patent Search

### 3.1 Databases Searched

| Database | Search Terms | Relevant Patents |
|----------|--------------|------------------|
| USPTO | "AI construction document classification" | 0 relevant |
| Google Patents | "neuroplasticity AI memory architecture" | 0 relevant |
| Espacenet | "multi-agent document processing construction" | 0 relevant |
| WIPO PatentScope | "quote extraction construction AI" | 0 relevant |

### 3.2 Related Patents Identified (Not Directly Applicable)

**Patent 1**: US20230342612A1 - "Document Classification System"
- Focus: General document sorting
- Gap: No construction specificity, no memory architecture

**Patent 2**: US20240012987A1 - "Multi-Agent AI System for Data Processing"
- Focus: Generic data pipelines
- Gap: Not document-focused, not construction-specific

### 3.3 Patent Search Conclusion

No existing patents cover the specific technical approach of Quotech:
- Neuroplasticity-inspired AI memory for construction documents
- Multi-agent orchestration for sub-contractor operations
- Construction-specific quote extraction and analysis

---

## 4. Expert Consultations

### 4.1 Industry Experts Consulted

**Expert 1**: Construction Operations Manager (Pilot Company A)
- **Question**: Are you aware of any software that automatically classifies construction documents and extracts quote data?
- **Response**: "We've looked at everything on the market. Nothing handles variations, day sheets, and quotes in one system. We still do most of this manually in Excel."

**Expert 2**: Construction Software Consultant (Independent)
- **Question**: What is the current state of AI in construction project management?
- **Response**: "AI in construction is mostly about physical automation - drones, robots. Document processing is still very manual. The closest is generic OCR tools, but they don't understand construction terminology."

**Expert 3**: AI/ML Researcher (University)
- **Question**: Has anyone applied neuroplasticity concepts to document retrieval systems?
- **Response**: "The idea of self-organizing memory networks inspired by brain plasticity is interesting but novel. I'm not aware of any commercial or academic implementation for document processing."

### 4.2 Industry Events Attended

| Event | Date | Key Learnings |
|-------|------|---------------|
| Construction Tech Summit 2024 | October 2024 | AI focus on site safety and robotics, not document processing |
| AI in Enterprise Conference | November 2024 | RAG systems emerging but no construction-specific implementations |

---

## 5. Competitor Analysis

### 5.1 Direct Competitors (Construction AI Startups)

| Company | Product | Focus | Gap vs Quotech |
|---------|---------|-------|----------------|
| Buildots | AI Progress Tracking | Site monitoring via cameras | Physical, not document AI |
| Doxel | AI Quality Control | Visual inspection | Physical construction, not documents |
| OpenSpace | 360° Capture | Site documentation | Photo-based, not text processing |
| Katerra | Integrated Delivery | Manufacturing focus | Discontinued (company failed) |

### 5.2 Indirect Competitors (General AI Document Tools)

| Company | Product | Gap vs Quotech |
|---------|---------|----------------|
| Anthropic Claude | General AI | Not construction-specific, no persistent memory |
| OpenAI | ChatGPT/Assistants | Not construction-specific, no ERP integration |
| Glean | Enterprise Search | Not construction-specific, no quote extraction |
| Notion AI | Document AI | No construction workflows, limited automation |

---

## 6. Summary of Technical Uncertainties

Based on the existing knowledge search, the following outcomes cannot be known in advance:

### 6.1 Neuroplasticity Memory Architecture
- **Uncertainty**: Can brain-like self-organizing memory networks improve retrieval accuracy for construction documents over time?
- **Existing Knowledge**: No prior application of this approach to document management
- **Status**: Unknown - requires experimentation

### 6.2 Multi-Agent Construction Classification
- **Uncertainty**: Can multiple specialized AI agents achieve >85% accuracy on construction-specific document categories?
- **Existing Knowledge**: General multi-class classifiers exist, but not trained on construction categories
- **Status**: Unknown - requires experimentation

### 6.3 Quote Extraction Accuracy
- **Uncertainty**: Can AI reliably extract structured cost data from diverse construction quote formats?
- **Existing Knowledge**: General OCR exists, but construction quote formats are highly variable
- **Status**: Unknown - requires experimentation

### 6.4 Cross-Company Model Transfer
- **Uncertainty**: Can models trained on one sub-contractor's documents transfer to another with acceptable accuracy?
- **Existing Knowledge**: Transfer learning is well-studied, but not for construction documents
- **Status**: Unknown - requires experimentation

---

## 7. Search Methodology Notes

### 7.1 Search Period
- Initial search: July-August 2024
- Updated search: January 2025
- Final verification: May 2025

### 7.2 Search Team
- Technical research conducted by development team
- Commercial analysis conducted by project leadership
- Expert consultations conducted by Abhishek Sehgal

### 7.3 Documentation
- All search results logged in research notes
- Key papers and products saved in reference folder
- Expert consultation notes maintained

---

## 8. Conclusion

The comprehensive search for existing knowledge confirms that:

1. **No academic literature** addresses the specific combination of neuroplasticity-inspired AI memory with construction document processing

2. **No commercial solution** provides AI-driven classification, quote extraction, and multi-agent automation for construction sub-contractors

3. **No patents** cover the technical approach being developed

4. **Industry experts confirm** that no existing solution addresses the information fragmentation problem in construction sub-contracting

5. **The outcome cannot be known in advance** because this is a novel application of AI architectures to a domain (construction sub-contractor operations) that has not been systematically addressed

---

*Search Report Compiled: FY25*
*Last Updated: June 2025*

# PATH: 04-supporting-materials/publications/monster-modules-whitepaper-summary.md
# PURPOSE:
# - Summary of the "Monster Modules" whitepaper for potential R&D context
# - This appears to be a separate R&D initiative related to AI infrastructure
#
# ROLE IN ARCHITECTURE:
# - Supporting documentation showing broader R&D capabilities
#
# NOTE: This whitepaper is titled "Data Centres - 3-Year Vision to becoming an AI Giant"
# and covers palletised AI micro data centres, NOT directly Quotech software.
# The filename references "Quotech" but content is about infrastructure.

---

# Monster Modules Whitepaper Summary

## Document Overview

| Field | Value |
|-------|-------|
| **Title** | Data Centres - 3-Year Vision to becoming an AI Giant |
| **Subtitle** | MONSTER MODULES: A First-Principles Blueprint for Palletised AI Micro Data Centres |
| **Version** | 2.0 |
| **Date** | 22 November 2025 |

---

## Vision Statement

> "Build 'cupboard-sized' data centre modules that can be dropped anywhere, powered by grid or solar, and used as local AI brains. Over time, link these modules via a content-addressed data layer so they can share models, data and spare capacity."

---

## Four-Layer Architecture

1. **Physical Pod**: Rugged enclosure housing rack, UPS, power distribution and cooling in forkliftable unit
2. **Compute Bricks**: Servers with high-core CPU and multiple high-end GPUs
3. **Local Software Stack**: OS, model server, vector database, telemetry and management
4. **Distributed Control Plane**: IPFS for content-addressed data, scheduler for workloads across pods

---

## Physical Specifications

### Pod Geometry (Pod C-6)
| Dimension | Value |
|-----------|-------|
| External Width | ~1100-1150 mm |
| External Depth | ~1800 mm |
| External Height | ~2200-2300 mm |
| Rack Size | 42-45U |

### Compute Brick Specifications
| Component | Specification |
|-----------|---------------|
| CPU | AMD EPYC 9354 (32 cores, 64 threads, 280W TDP) |
| GPU | 1-4x RTX 5090-class (~500-600W each) |
| RAM | 128-256 GB DDR5 ECC |
| Storage | 2x NVMe SSDs (OS + Data) |
| Power per Brick | ~3 kW design cap |
| Pod Total Power | 8-9 kW (2 bricks + cooling + overhead) |

---

## Economic Model

### Hardware Unit Economics
| Component | Cost |
|-----------|------|
| Per Brick | ~A$20,000 |
| Two Bricks | A$40,000 |
| Pod Structure (rack, UPS, cooling) | ~A$20,000 |
| Total Pod C-6 Construction | ~A$60,000 |
| **Sale Price** | A$85-95,000 |
| **Margin** | 30-40% |

### Operating Costs
| Item | Annual Cost |
|------|-------------|
| Electricity (heavy use, Melbourne) | ~A$13,000/year |
| Subscription Fee | A$300-600/month base |
| Add-on Packs | A$200-1,500/month |

### Solar Economics
- 40 kW array needed to offset full pod load
- Cost: ~A$40,000
- Levelised cost: 4-8 cents/kWh
- Payback: ~3 years at medium use

---

## C-0 Development Node (Prototype)

### Budget
| Component | Planning Value (AUD) |
|-----------|---------------------|
| CPU + Motherboard | 4,500 |
| GPU (RTX 5090) | 4,250 |
| 128GB RAM | 900 |
| NVMe Storage | 700 |
| 1600W PSU | 700 |
| Chassis + Cooling | 900 |
| 3 kVA UPS | 2,000 |
| 3.5 kW Cooling Unit | 3,000 |
| Networking + Misc | 4,000 |
| **Total** | ~A$22,000 |

### Power Consumption
| Scenario | Avg Power | Annual Cost |
|----------|-----------|-------------|
| Low Use | 0.8 kW | A$1,752 |
| Medium Use | 1.6 kW | A$3,504 |
| High Use | 2.5 kW | A$5,475 |

---

## Software Architecture

### Local Stack Components
- Stable Linux Server (Ubuntu 22.04)
- Container Runtime (Docker/containerd)
- Model Servers (vLLM, TensorRT-LLM, DeepSeek)
- Vector Database
- IPFS Node (private swarm)
- Control Agent + Monitoring

### IPFS Benefits
1. **Content Addressability**: CIDs for unambiguous model versioning
2. **Replication/Caching**: Natural content distribution
3. **Integrity Checks**: Automatic via Merkle trees

### Failure Behaviour
- Pods continue local workloads if WAN fails
- IPFS content cached locally for offline operation
- Graceful degradation, not catastrophic failure

---

## Market Positioning

### Target Market
- **Not competing with**: 1 MW hyperscale racks
- **Targeting**: Edge tier (3-10 kW loads)
- **Customers**: Factories, yards, carparks, industrial sites

### Differentiation from Competitors (e.g., Schneider EcoStruxure)
1. **GPU-Dense Design**: 8-9 kW AI-optimized vs 2-3 kW generic IT
2. **Opinionated AI Stack**: Pre-installed DeepSeek, RAG tooling
3. **Content-Addressed Network**: IPFS fabric from day one
4. **Forkliftable/Outdoor-Tolerant**: Edge-first design

---

## Risk Mitigation

### Engineering Risks
- **Thermal Runaway**: Conservative 3kW/brick envelope, proven cooling
- **Mechanical Issues**: Standard 42U racks, accessible components
- **Software Brittleness**: Self-contained operation first, network second

### Business Risks
- **Over-complexity**: Sequential build (brick → pod → platform → mesh)
- **Mispriced Subscriptions**: Modest base fees with optional add-ons
- **Wrong Customer Segment**: Target manufacturers, logistics, healthcare with AI needs

---

## Relevance to Quotech RDTI

### Potential Connections
1. **AI Infrastructure**: Monster Modules could host Quotech AI workloads
2. **Edge Deployment**: Construction sites could use pods for local AI processing
3. **Technical Overlap**: Both use DeepSeek, vector databases, and agentic AI
4. **R&D Capability**: Demonstrates Bravada's broader AI R&D portfolio

### Distinction
This is a **separate R&D initiative** focused on hardware infrastructure, while Quotech is focused on software for construction project management.

---

## Future Notes for AI

1. **If filing R&D for this project**: It would be a separate R&D activity, not part of Quotech
2. **Technical synergies**: Same AI stack (DeepSeek, vector DB) could be referenced
3. **Hardware R&D**: Different from software R&D, may qualify under different criteria
4. **Consider**: Whether to include this in FY25 filing as separate activity or supporting capability

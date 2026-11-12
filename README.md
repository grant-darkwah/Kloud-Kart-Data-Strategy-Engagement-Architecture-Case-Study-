# Kloud Kart — Data Strategy & Architecture Engagement

**Client:** Kloud Kart (E-Commerce Operations — Ghana & Nigeria Expansion)  
**Engagement Scope:** System Diagnosis, Target Architecture, 12-Month Roadmap, ADRs & Board Presentation  
**Operational Baseline:** ~4,000 orders/day | 15–20% YoY growth | 2-engineer data team capacity  

---

## Executive Overview
Kloud Kart’s rapid order growth and upcoming Nigeria market pilot have exposed critical bottlenecks across its single-server e-commerce infrastructure:
1. **Live Storefront Contention:** Heavy Monday morning reporting extracts overload the shared MySQL server, stalling live customer checkouts.
2. **Reporting Divergence & Oversells:** Operations and Finance pull spreadsheets at different cut-off windows without a single source of truth, causing conflicting weekly numbers and stock oversells.
3. **Regulatory Compliance Exposure:** Unencrypted customer exports stored across staff laptops and email threads create urgent exposure under Ghana’s Data Protection Act (Act 843) and an active 90-day Data Protection Commission (DPC) erasure inquiry.

This repository contains the complete advisory deliverables designed to stabilize daily operations, establish auditable PII governance, and prepare the platform for cross-border scale within a lean two-person data engineering team constraint.

---

## Engagement Deliverables

| # | Deliverable | File / Directory | Scope & Purpose |
| :--- | :--- | :--- | :--- |
| **1** | **Situation Diagnosis** | [`01-situation-diagnosis.md`](./01-situation-diagnosis.md) | Root-cause analysis across system performance, reporting divergence, Ghana Act 843 compliance risk, and financial exposure modeling[cite: 5]. |
| **2** | **Recommendation** | [`02-recommendation.md`](./02-recommendation.md) | Target data architecture blueprint, read-replica workload isolation, PII governance controls, and build-vs-buy trade-offs[cite: 5]. |
| **3** | **12-Month Roadmap** | [`03-12-month-roadmap.md`](./03-12-month-roadmap.md) | Phased 12-month execution plan sequenced for a 2-engineer data team ahead of the Nigeria pilot launch[cite: 5]. |
| **4** | **Architecture Decision Records** | [`04-adrs/`](./04-adrs/) | Three to six formal ADRs documenting core architectural choices, rejected alternatives, and operational trade-offs[cite: 5]. |
| **5** | **Board Deck** | [`05-board-deck/`](./05-board-deck/) | Executive presentation summarizing key findings, cost of inaction, target architecture, and delivery milestones for live board review[cite: 5]. |

---

## Repository Structure

```text
kloud-kart-data-strategy/
├── README.md
├── LICENSE
├── 01-situation-diagnosis.md
├── 02-recommendation.md
├── 03-12-month-roadmap.md
├── 04-adrs/
│   ├── ADR-001-read-replica-workload-isolation.md
│   ├── ADR-002-analytical-storage-and-cutoff-snapshots.md
│   ├── ADR-003-pii-governance-and-verifiable-erasure.md
│   └── ADR-004-multi-region-schema-strategy.md
└── 05-board-deck/
    └── kloud-kart-board-presentation.pdf

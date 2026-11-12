# Kloud Kart — Data Strategy & Architecture Engagement

**Client:** Kloud Kart (E-Commerce Operations — Ghana & Nigeria Expansion)  
**Engagement Scope:** System Diagnosis, Target Architecture, Governance & Delivery Roadmap  
**Operational Baseline:** ~4,000 orders/day | 15–20% YoY growth | 2-engineer data capacity  

## Overview
Kloud Kart’s rapid order growth and upcoming Nigeria pilot exposed critical bottlenecks across its single-server e-commerce stack: Monday reporting queries were stalling live customer checkouts, Operations and Finance reports diverged due to shifting cut-off windows, and exported customer CSVs created urgent compliance exposure under Ghana’s Data Protection Act (Act 843).

This repository contains the complete advisory deliverables designed to stabilize daily operations, establish a single source of truth, and prepare the platform for cross-border scale without over-engineering for a two-person data team.

## Engagement Deliverables
* **`01-situation-diagnosis.md`** — Root-cause analysis across system performance, reporting divergence, Act 843 compliance risk, and financial exposure modeling.
* **`02-architecture-recommendation.md`** — Workload isolation blueprint (read-replica decoupling), transformation pipeline design, and build-vs-buy trade-offs.
* **`03-governance-and-compliance.md`** — PII lifecycle controls, verifiable erasure workflows (90-day DPC window), and metric definitions.
* **`04-delivery-roadmap.md`** — Phased implementation plan sequenced for a 2-engineer team ahead of the Nigeria pilot launch.

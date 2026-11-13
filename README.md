# Kloud Kart: Data Strategy

A diagnosis, recommendation and 12-month roadmap for fixing Kloud Kart's data problems with a small, low-cost reporting setup.

**Prepared for:** Nana Adjei, Head of Operations
**Prepared by:** Grant Sarfo Darkwah
**Date:** 12 November 2026
**Status:** Draft for client review

---

## Summary


Kloud Kart is an online shop in Ghana handling about 4,000 orders a day, with 40 GB of data, one developer and two approved data hires. It has four problems:

Kloud Kart is an online shop in Ghana handling about 4,000 orders a day, with 40 GB of data, one developer and two approved data hires. It has four problems ranked by risks:


1. **Customer details are copied out of the shop and nobody counts the copies.** This matters most because of a live Data Protection Commission complaint.
2. **The shop and the reports share one machine.** Monday downloads slowed the shop twice last month.
3. **Operations and Finance get different numbers.** Each counts "an order" differently, and stock counts can go stale.
4. **One developer holds the whole system in his head.**

**Recommendation:** build one small reporting copy of the shop on the approved second server, refreshed nightly, with one agreed meaning for every number. Keep stock live inside the shop. Do not build a data lake, lakehouse or live data stream, and do not buy Snowflake or BigQuery this year.

**Estimated cost of the problems (base case):** about GHS 100,000 a year (low case about GHS 30,000, high case about GHS 660,000). Legal risk is not priced.

---

## Repository structure

```
kloud-kart-data-strategy/
├── README.md
├── LICENSE
├── 01-situation-diagnosis.md
├── 02-recommendation.md
├── 03-12-month-roadmap.md
├── 04-decisions/
│   ├── ADR-001.md
│   ├── ADR-002.md
│   └── ADR-003.md
├── 05-board-deck/
└── 06-improvement.md
```

| File | What it holds |
|---|---|
| `01-situation-diagnosis.md` | The four problems, ranked by board risk, with cost ranges, assumptions and open questions |
| `02-recommendation.md` | What to build, what not to build, running costs, hiring order and triggers for changing course |
| `03-12-month-roadmap.md` | Four quarters of dated deliverables, each with a check and an owner |
| `04-decisions/` | Architecture decision records (ADRs) for the key choices |
| `05-board-deck/` | Slides for the board conversation |
| `06-improvement.md` | Improvement beyond the brief: Customer Data Register and Deletion Drill |

---

## Recommended design

1. **Live mirror** of the shop on the second server, a few seconds behind. All reports and Monday downloads read from it.
2. **Nightly reporting set** rebuilt at 3 a.m. Accra time, cut off at midnight. "Orders placed" and "orders paid (after refunds)" are shown side by side.
3. **One door for customer details.** Reports show customer codes, not names or phone numbers, unless someone gives a reason. Every pull is logged.
4. **Stock stays live in the shop.** No report decides a sale.

### Deliberately not built

| Option | Decision |
|---|---|
| Data lake or lakehouse | No. Built for terabytes of untidy files; Kloud Kart's data is small and tidy |
| Real-time dashboards | No build, except one live screen ("orders so far today", "items low on stock") |
| Demand forecasting (ML) | Not this year. Revisit after two months of matching numbers |
| Snowflake or BigQuery | Not yet. The second server is approved and data-location rules need checking first |

### Triggers to revisit

- Data passes about 500 GB, or the nightly rebuild stops finishing by 7 a.m.: move to a cloud warehouse.
- A named decision needs data fresher than a day: give that report a live feed.
- Orders pass about 12,000 a day: review the whole design.

---

## Roadmap at a glance

| Quarter | Dates | Theme | Headline deliverables |
|---|---|---|---|
| Q1 | 12 Nov 2026 to 12 Feb 2027 | Protect customers and the shop | Real deadline confirmed by 20 Nov; customer file owners by 23 Nov; no double-selling by 11 Dec; complaint answered by 15 Jan (10 Feb at the very latest); Monday downloads stop slowing the shop by 11 Jan |
| Q2 | 15 Feb to 14 May 2027 | One set of numbers | One signed page of meanings by 5 Mar; same Monday report for everyone from 15 Mar; hand-built spreadsheets stop 19 Apr; customer lists from one logged place by 30 Apr |
| Q3 | 17 May to 13 Aug 2027 | Ready for Nigeria and the board | Nigeria's rules confirmed in writing by 28 May; Nigerian orders in the report from 7 Jun; deletion works end to end by 25 Jun; live board screen by 16 Jul |
| Q4 | 16 Aug to 12 Nov 2027 | Prove it holds, then decide what next | Report arrives without the developer 6 to 10 Sep; "Is it holding?" page by 1 Oct; numbers matched all quarter by 8 Nov; next step decided by 12 Nov |

If pressure rises, the order stays the same: customer data, then the shop, then the numbers.

### Hiring order

1. **Data engineer first** (builds and maintains the mirror and nightly job; ends the one-developer risk). Advert out 23 Nov, starts by 1 Feb 2027.
2. **Analyst second** (owns the numbers and the customer-data log). Advert out 1 Feb, starts by 19 Apr 2027.

---

## Assumptions and open items

The work is built from the client brief alone, with no data, staff interviews or access to shop records. Key items to confirm:

- The Commission's 90-day clock start date (the latest end date is 10 February 2027 if it started on 12 November 2026).
- The second server is big enough to hold both copies.
- Nigeria has not yet started collecting customer details.
- Basket size, slowdown length, share of shoppers who give up, weekly report hours and overselling rate (all estimates; one conversation with the developer replaces most of them).
- How Operations and Finance each define "an order" (assumed: placed vs paid after refunds).
- The legal points reflect a reading of Ghana's Data Protection Act, 2012 and **need a lawyer's confirmation** before anything goes to the Commission or the board.

---

## How to read this

- **Board or executive:** `02-recommendation.md`, then the table above.
- **Nana and operations:** `01-situation-diagnosis.md`, then `03-12-month-roadmap.md`.
- **Developer and data hires:** `02-recommendation.md` ("What we build"), `04-decisions/`, `06-improvement.md`.

---

## Contact

Grant Sarfo Darkwah

## License

<<<<<<< HEAD
See [LICENSE](LICENSE).
=======
See [LICENSE](LICENSE).
>>>>>>> e49bb7f7a65a521c9e21180bbf778e77813e7284

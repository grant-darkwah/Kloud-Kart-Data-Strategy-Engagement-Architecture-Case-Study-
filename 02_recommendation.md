Kloud Kart: Recommendation

Prepared for Nana Adjei, Head of Operations  |  Prepared by Grant Sarfo Darkwah  |  12 November 2026

## What I recommend

**Build one small, separate reporting copy of the shop on the approved second server, refreshed every night, with one agreed meaning for every number. Keep stock live inside the shop. Do not build a lake, a lakehouse or a live data stream, or buy Snowflake or BigQuery this year.**

This fixes the three things that hurt: Monday downloads slowing the shop, Operations and Finance disagreeing, and customer files copied with no count. It fits 40 GB of data, 4,000 orders a day, one developer and two hires. At 20% growth the data reaches only about 100 GB in five years, which is small for one server.

## What we build

1.    **A live mirror of the shop on the second server,** a few seconds behind. All reports and Monday downloads read from it, never from the shop.

2.    **A reporting set rebuilt at 3 a.m. Accra time,** cut off at midnight, so everyone sees the same snapshot. Both meanings of “an order” are shown side by side: **placed** (the customer clicked buy) and **paid** (after refunds).

3.    **One door for customer details.** Reports show customer codes, not names or phone numbers, unless someone gives a reason. Every pull is logged, so we can count copies and prove deletion.

4.    **Stock stays live in the shop.** The shop checks stock at the moment of purchase. No report is ever used to decide a sale.

## What we are not building

|**On the wish list**|**Decision**|**Why, at Kloud Kart’s size**|
|---|---|---|
|Data warehouse|Yes, in its smallest form (step 2)|Tidy tables, one definition each, daily refresh|
|Lakehouse or data lake|No|Built for terabytes of untidy files. Ours is small and tidy, and it needs engineers we cannot hire|
|Real-time dashboards|No build, but one live screen|The mirror is seconds behind, so “orders so far today” and “items low on stock” can run from it without touching the shop. Nothing else in the brief needs minute-by-minute numbers|
|Demand forecasting with ML|Not this year|Needs months of clean history with agreed definitions. Revisit after two months of matching numbers|
|Buy Snowflake or BigQuery|Not yet|The second server is already approved. A cloud bill is in dollars and varies, which made Finance flinch. The team would learn a new platform during urgent fixes. Where customer data may sit needs checking first|

## What it costs to run

|**Item**|**Cost**|
|---|---|
|Second server|Already approved. Price not given, so not counted|
|Software|GHS 0 (open-source tools)|
|Extra backup space|My estimate: a few hundred cedis a month. Get a quote|
|Set-up|About six weeks of the developer’s part-time, shared with the first hire|
|Lawyer check of the deletion process|Unknown. Get a quote|
|The two data hires|Already budgeted. The main running cost|

## Who we hire, in order

5.    **A data engineer first** (builds and looks after the pipes). Nothing works without the mirror and nightly job, and this ends the one-developer risk. First 90 days: stand up the mirror, move Monday downloads onto it, write down how it all works.

6.    **An analyst second** (owns the numbers). Agrees one meaning per number with Nana and Finance, builds the reports, runs the customer-data log.

## If the board challenges this

•      **“Is this real-time?”** For stock, yes, because it must be. For reports, no. Ask which decision would change with minute-fresh numbers. If there is an answer, we add it.

•      **“Is this just the cheap option?”** It is the cheapest answer to today’s problems and will not scale forever. That is why the triggers below exist.

•      **“What about Nigeria?”** It cuts the slowdown risk. The legal side needs a lawyer before Nigerian customer details are collected.

## What would change my mind

•      Data passes about 500 GB, or the nightly rebuild stops finishing by 7 a.m.: move to a cloud warehouse.

•      A named decision needs data fresher than a day: give that one report a live feed.

•      Orders pass about 12,000 a day (three times today): review the whole design.

## What I decided where the brief was silent

•      The second server is big enough to hold both copies. **To confirm.**

•      Reports are ready by 7 a.m., cut off at midnight.

•      Personal details are hidden in reports by default.

•      Everything stays on our own server for now. Nigerian customer data waits for a lawyer’s confirmation.
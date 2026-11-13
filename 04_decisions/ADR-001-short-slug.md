# ADR-001: Run all reports from a live copy on the second server, in a small reporting database we run ourselves

- **Status:** Accepted
- **Date:** 2026-11-12
- **Decision owner:** Grant Sarfo Darkwah

## Context

Twice last month a Monday export slowed the live shop to a crawl. The shop and its database share one machine. The shop takes about 4,000 orders a day (roughly 167 an hour on average), the database is about 40 GB, and Monday's exports are a few hundred thousand rows. A second server is already approved. The team is one developer, and nobody has run a data warehouse. The wish list (a warehouse or lakehouse, Snowflake or BigQuery) came from investor and developer comments, not a requirements process, so this was open. Nana is unavailable, so I decided and am recording why.

## Decision

Put a live copy of the shop's database on the approved second server, build a small reporting database from it every night on the same server, and point every report and Monday download at those two, never at the shop.

## Alternatives considered

### Alternative A: Keep reports on the shop's machine and run them off-peak

- **How it would work:** Move Monday's exports to 5 a.m. and keep one machine.
- **Why it is attractive:** It costs nothing, needs no new skills, and could start on Monday 23 November. It would stop most Monday-morning clashes.
- **Why rejected:** The shop and the reports still share one machine, so this only moves the clash to another hour. Growth of 15 to 20 percent a year and the Nigeria pilot shrink the quiet hours. It also does nothing about Operations and Finance getting different numbers. I use it only as a stop-gap until the live copy is ready.

### Alternative B: Buy a cloud warehouse (Snowflake or BigQuery)

- **How it would work:** Send the shop's data to a cloud service and run all reports there.
- **Why it is attractive:** There is no server to look after, it grows without us, the developer wants it, and the tools are strong. Storage for 40 GB is cheap on these services.
- **Why rejected:** The second server is already approved, so the cheaper answer is already paid for. A cloud bill is in dollars and varies with use, which is what made Finance flinch (I have not priced it). The team would learn a new platform while fixing urgent problems. And where 300,000 people's details may be held needs a lawyer's view before any move, while a complaint is open.

### Alternative C: Build a lakehouse

- **How it would work:** Store raw files in cheap cloud storage and query them with a lakehouse engine.
- **Why it is attractive:** It handles any kind of data and scales to huge sizes, and it sounds future-proof to investors.
- **Why rejected:** It is built for terabytes of mixed files. Kloud Kart has about 40 GB of tidy tables, which reaches only about 100 GB in five years at 20% growth. It needs engineers we cannot hire with two hires. And raw files multiply copies of customer details, which is the problem behind the complaint.

## Consequences

- **What this buys:** The shop gets its own machine back. Everyone reads the same nightly snapshot, ready by 7 a.m. Licences cost nothing. It fits one developer plus two hires.
- **What this costs:** A second machine to look after, about six weeks of the developer's part-time to set up, and a ceiling: Kloud Kart will outgrow it. Reports are up to a day old.
- **What it costs the client if I am wrong:** If the second server is too small or the live copy falls behind, the slowdowns continue. At my base estimate that is about GHS 4,200 a month in lost sales (range roughly GHS 1,300 to 40,000), and the Monday 11 January date moves.
- **What would make me revisit this:** Data passing about 500 GB, the nightly rebuild not finishing by 7 a.m., orders passing about 12,000 a day, or the second server turning out too small.

## What this survives

- **Orders triple to about 12,000 a day:** The shop is unaffected, because reports never touch it. The nightly rebuild gets longer and has to be watched.
- **Nigeria pilot volume:** Same answer. Extra volume lands on the shop, not on the reports.
- **Growth to about 100 GB:** It still fits comfortably on one server.
- **Does not survive:** The second server failing with no backup. Reports would stop, though the shop would not. 
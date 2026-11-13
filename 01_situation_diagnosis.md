# Kloud Kart: Situation Diagnosis

Prepared for Nana Adjei, Head of Operations Prepared by Grant Sarfo Darkwah | 12 November 2026

## The short version

Kloud Kart has four problems. Three of them come from one decision nobody ever made: **where company and customer data is allowed to live, and who is allowed to take it out.** The fourth is that only one person understands the system.

- **Customers' personal details are being copied out of the shop and nobody is counting the copies.** Every Monday download, every marketing list and every emailed sheet is another copy. If a customer asks to be deleted, we can delete them from the shop, but we cannot prove they are gone everywhere. We have a deadline to answer the Data Protection Commission, and this is the problem that can hurt us there.
- **The shop and the reports share one machine.** When Monday's big downloads run, the shop slows down while customers are trying to pay. This happened twice last month.
- **Operations and Finance get different numbers because they are not measuring the same thing.** They pull files at different times, and each spreadsheet counts "an order" differently. Nobody is doing anything wrong; the company has simply never written down one meaning for each number.
- **One developer holds all of this in his head.** Every fix above depends on one person.

**What it costs (best estimate, with ranges):** roughly GHS 100,000 a year in lost sales, oversold orders and wasted staff hours at today's size, on my base assumptions, with a low case near GHS 30,000 and a high case near GHS 660,000. The legal risk is not priced, because I cannot verify the penalties (see "What I could not verify"). Every figure rests on assumptions that are labelled, and one phone call to the developer would replace most of them with real numbers.

**What is urgent:** the customer-data problem, because of the deadline. If the clock started today, the 90 days end on 10 February 2027. It probably started earlier, so the real date is sooner. Please Nana, confirm the start date.

## The four problems, ranked by risk to the board conversation

Ranked by how badly each could damage the company in front of the board and investors, not by how annoying it is day to day.

|   |   |   |   |   |
|---|---|---|---|---|
|Rank|Problem in plain words|Why it matters to the board|Best-estimate cost per year|How sure am I|
|1|Customer details are copied out of the shop and not counted|Hard deadline, legal consequences, hard to explain to investors|Not priced (needs counsel)|High that copies exist, low on how many|
|2|Monday downloads slow the live shop|Lost sales now; gets worse with growth and the Nigeria launch|About GHS 50,000 (range 16,000 to 480,000)|Medium|
|3|Operations and Finance numbers disagree, and stock can go out of date|The board gets two answers to one question; "real-time dashboards" would just show the wrong number faster|About GHS 52,000 (range 14,000 to 181,000)|Medium on labour, low on overselling|
|4|One developer, nobody else who knows the system|Every fix depends on one person staying and not being overloaded|Not priced|High|

## Problem 1: Customer details are copied out of the shop and nobody counts the copies

**What people see:** The company is answering a Data Protection Commission complaint about a deleted customer's data, and leadership cannot say where that customer's details still sit.

**What is actually producing it:** The only way anyone gets information out of the shop is by downloading a file. There is no record of who downloaded what, no rule for how long a file may be kept, and no rule for deleting it. Marketing's list alone holds about 300,000 people. Each time it is exported, that is a copy of up to 300,000 people's names, phone numbers and addresses, saved on a laptop or sent by email. Deleting a customer in the shop does nothing to any of those files.

**Where a deleted customer's details could still be sitting:**

- Monday export files on staff laptops
- Email attachments, including sent items and forwarded copies
- WhatsApp or shared-drive copies
- Marketing's email or SMS tool
- The shop's backups
- Delivery partners and the payment company

Proving deletion means checking all of these, not only the shop.

**What it costs:** I have not put a number on this. The possible fines, legal fees and customer compensation depend on how the Commission and a lawyer read the law, and I cannot verify those from here. The cost of **fixing** it is small by comparison: a few days of staff time (see the first two weeks below). That gap is the argument for doing it first.

**The Nigeria pilot makes it worse.** Nigerian customers' details would flow into the same untracked files, and Nigeria has its own data protection law. I understand Ghana's law requires us to respect the home country's rules when we process a foreign customer's data. Counsel needs to confirm this before the pilot starts taking real customer data.

**First two weeks (containment, not the full fix):**

1. **Stop the bleeding.** From today, no customer file leaves the shop without a named owner and a line in a shared log (who, when, why, where saved).
2. **Find the copies.** Ask Operations, Finance and Marketing each to list every place they keep customer files, including email and WhatsApp.
3. **Find the deleted customer everywhere.** Check the shop, backups, the marketing tool, delivery partners and the payment company.
4. **Write down what was found and removed, with dates.** That dated record is our evidence for the Commission.
5. **Ask a lawyer** to confirm the real deadline and what the Commission expects in our reply.

**How sure am I:** High that untracked copies exist (the brief says so directly). Low on how many, because nobody has counted yet.

## Problem 2: The shop and the reports share one machine

**What people see:** Twice last month, a Monday download made the live shop crawl.

**What is actually producing it:** The shop and the company's reporting both use the same machine. Think of one till where customers pay and the manager does a full stock-take at the same counter. Monday's download asks the database to read hundreds of thousands of rows. While it does, the machine has less memory, disk speed and processing power left for shoppers. The slowdown is not a freak event; it is what happens every time a big report runs on the machine that serves customers.

**What it costs.** I do not know the length of the slowdowns, the share of shoppers who gave up, or the typical basket. So here are three scenarios. At 4,000 orders a day, the shop takes about 167 orders an hour on average.

|   |   |   |   |   |
|---|---|---|---|---|
|Scenario|Slow time per month|Shoppers who give up|Basket size|Sales lost per year|
|Low|2 hours|10%|GHS 40|about GHS 16,000|
|Base|2 hours|25%|GHS 50|about GHS 50,000|
|High|6 hours|50%|GHS 80|about GHS 480,000|

These are sales, not profit. They also leave out customers who never come back, and they grow with the company. At 15 to 20 percent growth, plus the Nigeria pilot, a monthly problem can become a weekly one.

**How to replace my guesses with facts:** The shop's own records show how many orders were placed during the two slow hours compared with a normal Monday. One question to the developer settles most of this table.

**Good news:** A second server is already approved. Moving reporting onto it separates the till from the stock-take. This is the fastest fix in the whole diagnosis.

**How sure am I:** Medium. I am confident the cause is the shared machine. I am less sure of the size of the loss.

## Problem 3: Two sets of numbers, and stock that can go out of date

**What people see:** Nana's Monday numbers and Finance's numbers never match.

**"The reports disagree" is the symptom. Three things are producing it:**

1. **Different pull times.** The shop keeps changing all morning. A file pulled at 8:00 and a file pulled at 8:15 are different pictures of the business, even if both are correct.
2. **Different meanings.** Nobody has written down what counts as "an order" or "stock available." I assume Operations counts an order when the customer clicks buy, and Finance counts it when the payment clears and refunds are taken off. Both can be right, but they are different numbers with the same name.
3. **Different spreadsheets.** Each person rebuilds the report by hand in their own workbook. Every manual step is a chance for a quiet mistake, and nobody can check anyone else's.

**Why this matters to the board:** The board wants "real-time dashboards." A dashboard built on numbers that do not agree just shows the wrong answer faster. The meanings come first, the screens second.

**What it costs, part one: staff time.** Nana and Finance spend time every week exporting, cleaning and reconciling. I assume between 3 and 12 hours combined.

|   |   |   |   |
|---|---|---|---|
|Scenario|Hours a week|Cost per hour|Cost per year|
|Low|3|GHS 40|about GHS 6,000|
|Base|6|GHS 50|about GHS 15,600|
|High|12|GHS 60|about GHS 37,000|

**What it costs, part two: overselling.** The brief says stock counts that go stale are how the company sells items it no longer has. I do not know how often this happens. I priced the cost of an oversold order as the refund fee, the support time and the damaged goodwill, not as lost profit, because that stock was never really there to sell.

|   |   |   |   |
|---|---|---|---|
|Scenario|Oversold orders a day|Cost per oversold order|Cost per year|
|Low|4 (0.1%)|GHS 5|about GHS 7,000|
|Base|10 (0.25%)|GHS 10|about GHS 36,000|
|High|20 (0.5%)|GHS 20|about GHS 144,000|

Customers who are let down once and leave are real but not included.

**One thing I could not pin down:** I do not know _where_ the out-of-date stock count lives. The live shop may read its own stock correctly, and the stale number may sit in a spreadsheet someone uses to restock or promise items. That is the first question for the developer.

**How sure am I:** Medium on the staff time, low on overselling until we know where the stale count lives.

## Problem 4: One developer holds everything

**What people see:** Nothing yet. It looks fine until it is not.

**What is actually producing it:** One developer knows the shop, the database and the exports. Nobody else has run a data warehouse or written code in Python at work. The company has budget for two data hires, but until they are in place, every fix in this document runs through one person who is also keeping the shop alive.

**What it costs:** Not priced. The risk is delay (fixes queue behind daily shop work) and dependency (if he leaves or is unavailable, nobody can step in).

**What it means for the plan:** Fix the problems that do not need new skills first: stop the copies, separate the reports from the shop, agree the number meanings. Do not start a project that only the developer can run.

## What would change this ranking

- If the real Commission deadline is earlier than I think, Problem 1 gets even more urgent.
- If the slowdown records show the slow hours were much longer than two, Problem 2 moves above Problem 3 on money alone.
- If most overselling comes from a spreadsheet and not from the live shop, Problem 3 becomes mainly a process fix, not a technology fix.
- If investors want a specific live number on a screen soon, Problem 3 jumps in urgency, because that screen needs the meanings agreed first.

## What I could not verify

This diagnosis is built only from the brief. No data, no staff interviews and no access to the shop's records. The items below are things I assumed, and what happens if I am wrong.

|   |   |   |
|---|---|---|
|What I assumed|Why|If I am wrong|
|Average basket is about GHS 50|The brief does not give one|Problem 2 and 3 costs scale up or down directly|
|Two slowdowns of about an hour each|The brief says "twice," not how long|Problem 2 cost scales with duration|
|25% of shoppers give up during a slowdown|Industry-style guess|Problem 2 changes in proportion|
|6 hours a week of manual report work|The brief does not give hours|Problem 3 labour changes in proportion|
|0.25% of orders oversold|The brief names the cause, not the rate|Problem 3 overselling cost changes in proportion|
|Operations counts an order at click, Finance at payment|Common difference, not confirmed|The fix changes to the real difference|
|Customer files sit on laptops and in email|The brief says exports and untracked lists|We may find more places, or fewer|
|The Data Protection Commission deadline is 90 days from today at the latest|The brief gives the length, not the start|A real earlier start shortens the time to act|
|Penalties are not priced|I cannot verify them|Counsel will give a real range|

I also have not checked the exact legal wording. The legal points here are my reading of Ghana's Data Protection Act, 2012 and need a lawyer's confirmation before anything goes to the Commission or the board.

## Questions I would have put to Nana, and what I decided in her absence

Nana could not be asked. Each answer below is a working decision. If she disagrees, the plan changes the way the last column says.

|   |   |   |
|---|---|---|
|What I would ask|What I decided for now|If she disagrees|
|When Monday's numbers disagree with Finance's, which decisions get delayed or reversed, and what happens to stock buying if nothing changes for 90 days?|Finance delays cash approval and Operations delays reordering, because these reports feed manual checks, not automatic restocking|If restocking is automatic, the stakes are higher and Problem 3 ranks above Problem 2|
|How do you and Finance each define "a completed order" and "stock available", especially for unpaid mobile-money orders, cancellations and returns?|Two named versions: "orders placed" (Operations) and "orders paid, after refunds" (Finance), both shown, never blended|If the difference is something else, the agreed meanings change|
|Apart from stock counts on the live shop, which reports really need to update during the day, and which can be one trusted morning summary?|Only stock on the shop must be live; every report can refresh once a day|If a report needs live data, it gets its own, separate fix|
|Where do Monday downloads, refund sheets and delivery lists get saved or emailed, and how long do they stay on laptops?|They sit on laptops and in email, with no end date|If files are better controlled, Problem 1 shrinks|
|Will Nigerian orders ship from Accra stock or a separate Lagos warehouse, and what daily volume ends the pilot?|Same database and workflow as Ghana at first|A separate warehouse means separate stock records and more complexity|
|Once the manual downloads stop, who will sign off the agreed number meanings with Finance, so the data hires are not refereeing every Monday?|Nana and the Finance lead own the meanings together; the data hires own making them happen|If nobody owns it, the disagreement comes back|
|Who decides what customer data Marketing may export, and when does it get deleted?|No single owner today; I assume Nana until told otherwise|The owner needs the first-two-weeks log to work|
|Is the Commission complaint's 90-day clock already running, and from what date?|Assumed at most 90 days from today|An earlier date means the first two weeks cannot wait|
# Trial: Cloud spend variance bridge, run on its invented example

- **Product:** Claude, run in Claude Code

Model: Claude Sonnet 5.5 (model ID claude-sonnet-5-5). The assistant that ran this trial did not write the template.

Date: 2026-11-10

The inputs are the invented example in `public/example.md` (Software Company Q, a made-up software company). No client data was used.

## Inputs used

All five inputs from "The inputs" section of `public/example.md`: the settings (October 2026, prior month September 2026, USD, thresholds 1,000 and 10%, shared tag `shared`), the billing export for both months (23 rows), the October budget (7 services), the cost-owner mapping (2 accounts) and the usage figures (5 services). The example's own bridge was not read until after the output below was produced.

## What came out

The instruction block and the output format were followed as written. The full output:

```
CLOUD SPEND VARIANCE BRIDGE: 2026-10

For: Finance lead and Engineering manager. Currency USD. Budget for 2026-10; billing export for 2026-10 and 2026-09. A move is material at 1,000 and 10% or more.

Result: Budget 44,000. Actual 51,600. Variance +7,600 (17.3%). Prior month 47,030, so the month rose 4,570 (9.7%).

Bridge:
Budget 44,000
Compute (Platform team): +6,000
Machine learning training (Data team): -1,900
Logging and monitoring (Platform team): +1,300
Object storage (Data team): +1,200
Budgeted services within the threshold (3): +650
Services not in the budget (1): +350
Actual 51,600
Check: 44,000 + 6,000 - 1,900 + 1,300 + 1,200 + 650 + 350 = 51,600; export rows total 51,600.

Material moves (4):
1. Compute (budget owner Platform team): budget 20,000, actual 26,000, variance +6,000 (30.0%). Prior month 21,500; change +4,500 (20.9%). Cost owners: Platform team 19,400 (tag); Data team 3,900 (mapping); unallocated 2,700 (no tag, account not mapped). New this month: dev-sandbox 2,700. Usage: vCPU-hours, 310,000 to 312,000 (0.6%, flat); cost per unit 0.0694 to 0.0833 (20.2%, up).
2. Machine learning training (budget owner Data team): budget 5,000, actual 3,100, variance -1,900 (-38.0%). Prior month 4,800; change -1,700 (-35.4%). Cost owners: Data team 3,100 (tag). New this month: None. Usage: GPU-hours, 960 to 620 (-35.4%, down); cost per unit 5.00 to 5.00 (0.0%, flat).
3. Logging and monitoring (budget owner Platform team): budget 3,000, actual 4,300, variance +1,300 (43.3%). Prior month 3,800; change +500 (13.2%). Cost owners: shared 4,300 (tag). New this month: None. Usage: GB ingested, 7,600 to 8,600 (13.2%, up); cost per unit 0.50 to 0.50 (0.0%, flat).
4. Object storage (budget owner Data team): budget 4,000, actual 5,200, variance +1,200 (30.0%). Prior month 4,400; change +800 (18.2%). Cost owners: Data team 4,600 (tag); Platform team 600 (mapping). New this month: None. Usage: GB-months, 44,000 to 52,000 (18.2%, up); cost per unit 0.1000 to 0.1000 (0.0%, flat).

Within the threshold: Managed database, +400; Data transfer, +250; Support plan, 0.

Not in the budget: Container registry, 350, Platform team (tag).

Costs by cost owner: Platform team 30,850 (59.8%); Data team 12,250 (23.7%). Shared 5,800 (11.2%). Unallocated 2,700 (5.2%).

Shared costs: Logging and monitoring, 4,300; Support plan, 1,500. Total 5,800.

Unallocated costs: Compute, dev-sandbox, 2,700. Total 2,700 (5.2%).

No usage figures: Managed database; Support plan; Container registry.

Questions for engineering:
1. Compute usage was flat (0.6%) while its cost per vCPU-hour rose 20.2%; what else changed in how the service is run or billed?
2. Machine learning training used 35.4% fewer GPU-hours than in September at the same cost per GPU-hour; is the lower use lasting or a matter of timing?
3. Logging and monitoring ingestion rose 13.2% at the same cost per GB; what drove the higher use, and is it expected to continue?
4. Object storage usage rose 18.2% at the same cost per GB-month; what drove the higher use, and is it expected to continue?
5. The dev-sandbox account has 2,700 of Compute in October and none in September; what runs there, and was it planned?

Questions for finance:
1. Who should own the 2,700 of unallocated Compute in dev-sandbox?
2. Logging and monitoring, 4,300, is shared and 1,300 over budget; should it be divided between teams, and how?
3. Did the October budget expect the new dev-sandbox Compute cost of 2,700?
4. Container registry, 350, is not in the budget; is it a new service or a renamed budget line?

Decisions for people (6):
1. Compute is 6,000 over a budget of 20,000 (30.0%). Choices: accept the variance, change the budget, or ask engineering to look further. The finance lead and the Platform team approve any change in spend.
2. Machine learning training is 1,900 under a budget of 5,000 (38.0%). Choices: accept the variance, change the budget, or ask engineering to look further. The finance lead and the Data team approve any change in spend.
3. Logging and monitoring is 1,300 over a budget of 3,000 (43.3%). Choices: accept the variance, change the budget, or ask engineering to look further. The finance lead and the Platform team approve any change in spend.
4. Object storage is 1,200 over a budget of 4,000 (30.0%). Choices: accept the variance, change the budget, or ask engineering to look further. The finance lead and the Data team approve any change in spend.
5. Unallocated cost is 2,700 (5.2% of the actual), all Compute in dev-sandbox. Choices: name an owner, or leave it unallocated for now. The finance lead and the service owner approve any change in spend.
6. Container registry, 350, is not in the budget. Choices: add it to the budget, or confirm it is a renamed line. The finance lead and the Platform team approve any change in spend.

Not supplied or checked: No cloud account was read, no resource was inspected, operational dependencies were not checked and no cause was established. All optional inputs were supplied.

Every figure traces to the billing export for 2026-09 and 2026-10, the budget for 2026-10 and the files supplied (settings, cost-owner mapping, usage figures). The bridge changes no records, touches no cloud account and sends nothing.
```

## What was observed

- Every part of the output format was produced. Nothing in the inputs triggered a stop condition, and the bridge added up on the first pass (44,000 + 7,600 = 51,600, equal to the export total).
- Every figure matches the published example. The differences are small and are about wording and order, not numbers:
  - Within the threshold: the example lists Data transfer, Managed database, Support plan (alphabetical); this run listed them largest variance first. The template does not say how to order that list.
  - No usage figures: the example lists Container registry first (alphabetical); this run followed the order of the budget, with the unbudgeted service last.
  - The example prints the one-decimal cost per unit as "0.10" for Object storage; this run printed "0.1000", because the procedure says four decimal places when the result is under 1. The example is inconsistent with its own template on that line (it also prints 0.50 for Logging, which is under 1). The run itself was not consistent either: its own output prints 0.50 to 0.50 for Logging and monitoring, which is under 1 and should have had four decimals. That is a deviation by the run, not only by the example.
  - Questions: the same nine questions, in a different order. The example puts the dev-sandbox engineering question second and the finance one first; this run put the move-by-move questions first and the new-account question last.
  - Decisions: the same six. This run added the percent to each and, for the unallocated decision, named the finance lead and the service owner as approvers (the template asks for both to be named); the example says only "The finance lead decides."
  - The example's trace line does not list the file types; this run added the settings, mapping and usage files.
- Facts in either output that are not in the inputs: none found. The service owners named in the decisions come from the budget's `owner` column. The example uses "Finance lead" and "Engineering manager" as the names of the two people, which is how the settings give them.
- Places where the instructions were ambiguous and a guess was needed:
  - Cost per unit change: computed from the unrounded values this gives +20.2% for Compute; from the printed, rounded values (0.0694 to 0.0833) it gives +20.0%. The template does not say which. The example uses the unrounded values, as this run did.
  - How to order the cost owners in "Costs by cost owner" (only "shared and unallocated last" is stated); this run put the largest first, as the example does.
  - How to order the within-threshold list, the "No usage figures" list and the questions (see above). "Ties in service order" for material moves does not say whose order: alphabetical or the order of the budget.
  - "New this month" is defined for an account, but the example treats it as an account that has cost in the service in October and none in September. The dev-sandbox account has no rows at all in September, so it is new either way; a case where an account existed in September in another service would be unclear.
  - How to show a shared row in a material move's "Cost owners" list: the format offers "tag", "mapping" and "no tag, account not mapped". This run wrote "shared 4,300 (tag)", as the example does, because the shared tag is a tag.
  - Whether a question to finance about a new account (was it budgeted) should come before or after the unallocated question: the template gives the order of rules, not of the list.
  - The instruction block for the assistant leaves out some rules that are in the procedure: rounding halves up, the four-decimal rule for cost per unit, the 2% flat rule's "either direction" and the prior-month-missing behaviour. A run that used only the fenced block would have to guess the decimals for cost per unit. The stop condition for a duplicate row is in the block.
  - The format line "Services not in the budget ([n]): [+variance]" shows a plus sign only; a credit-only unbudgeted service would have a negative figure.
- Nothing was cut from the output above.
- This was one run, by one model, on one invented example. It shows that the instructions can be followed to the published result; it does not show how the template performs on a real billing export, and no client data was used.

## Changes after this run

The output above is the record of this run and has not been altered. After an independent review the same day, the template and its example were edited without a rerun:

- The instruction block now carries the rounding rule, the cost-per-unit decimals, the 2% flat test in either direction, the prior-month-missing behaviour and the stops for a missing month, currency or budget.
- "Service order" now means alphabetical, and it orders the within-threshold, not-in-the-budget, shared, unallocated and no-usage lists. Cost owners go largest first, shared and unallocated last. Questions follow the order of the rules in step 11, so the example's engineering questions now read in the order this run produced them.
- The unallocated decision names the finance lead as the person who settles it, with the service owner approving any change in spend.
- "New this month" is defined within the service, and the unbudgeted-service format line allows a minus sign.
- The example now prints 0.5000 and 0.1000 for cost per unit, and the within-threshold list uses commas.

A rerun after those edits is recorded below. The first run's output and observations above are unchanged.

## Second run, on the edited wording

Model: Claude Sonnet 5.5 (model ID claude-sonnet-5-5). Date: 2026-11-10. The same invented inputs.

This second run was made by the assistant that applied the later review's small edits, not by a fresh assistant. It had already read the example and the first run, so it is not a blind run and is weaker evidence than the first. It applied the edited instruction block and output format to the five inputs and checked its figures against the inputs, not against the example. A further edit then changed the format line for a material service not in the budget; the example has none, so that rule has not been exercised by any run.

The edits it carries: a material service not in the budget gets its own step and one decision and is left out of the grouped step; the flat, up or down word is printed on usage as well as on cost per unit; the unallocated total is printed with its share of the actual; the instruction block states the question rules, the budgeted service with no export rows and the "also had cost in" note.

The full output:

```
CLOUD SPEND VARIANCE BRIDGE: 2026-10

For: Finance lead and Engineering manager. Currency USD. Budget for 2026-10; billing export for 2026-10 and 2026-09. A move is material at 1,000 and 10% or more.

Result: Budget 44,000. Actual 51,600. Variance +7,600 (17.3%). Prior month 47,030, so the month rose 4,570 (9.7%).

Bridge:
Budget 44,000
Compute (Platform team): +6,000
Machine learning training (Data team): -1,900
Logging and monitoring (Platform team): +1,300
Object storage (Data team): +1,200
Budgeted services within the threshold (3): +650
Services not in the budget (1): +350
Actual 51,600
Check: 44,000 + 6,000 - 1,900 + 1,300 + 1,200 + 650 + 350 = 51,600; export rows total 51,600.

Material moves (4):
1. Compute (budget owner Platform team): budget 20,000, actual 26,000, variance +6,000 (30.0%). Prior month 21,500; change +4,500 (20.9%). Cost owners: Platform team 19,400 (tag); Data team 3,900 (mapping); unallocated 2,700 (no tag, account not mapped). New this month: dev-sandbox 2,700. Usage: vCPU-hours, 310,000 to 312,000 (0.6%, flat); cost per unit 0.0694 to 0.0833 (20.2%, up).
2. Machine learning training (budget owner Data team): budget 5,000, actual 3,100, variance -1,900 (-38.0%). Prior month 4,800; change -1,700 (-35.4%). Cost owners: Data team 3,100 (tag). New this month: None. Usage: GPU-hours, 960 to 620 (-35.4%, down); cost per unit 5.00 to 5.00 (0.0%, flat).
3. Logging and monitoring (budget owner Platform team): budget 3,000, actual 4,300, variance +1,300 (43.3%). Prior month 3,800; change +500 (13.2%). Cost owners: shared 4,300 (tag). New this month: None. Usage: GB ingested, 7,600 to 8,600 (13.2%, up); cost per unit 0.5000 to 0.5000 (0.0%, flat).
4. Object storage (budget owner Data team): budget 4,000, actual 5,200, variance +1,200 (30.0%). Prior month 4,400; change +800 (18.2%). Cost owners: Data team 4,600 (tag); Platform team 600 (mapping). New this month: None. Usage: GB-months, 44,000 to 52,000 (18.2%, up); cost per unit 0.1000 to 0.1000 (0.0%, flat).

Within the threshold, in service order: Data transfer, +250; Managed database, +400; Support plan, 0.

Not in the budget, in service order: Container registry, 350, Platform team.

Costs by cost owner: Platform team 30,850 (59.8%); Data team 12,250 (23.7%). Shared 5,800 (11.2%). Unallocated 2,700 (5.2%).

Shared costs: Logging and monitoring, 4,300; Support plan, 1,500. Total 5,800.

Unallocated costs: Compute, dev-sandbox, 2,700. Total 2,700 (5.2% of the actual).

No usage figures, in service order: Container registry; Managed database; Support plan.

Questions for engineering:
1. Compute usage was nearly flat (0.6%) but its cost per vCPU-hour rose 20.2%; what else changed in how the service is run or billed?
2. Machine learning training used 35.4% fewer GPU-hours than in September; is the lower use lasting or a matter of timing?
3. Logging and monitoring ingestion rose 13.2% at the same cost per GB; what drove the higher use, and is it expected to continue?
4. Object storage rose 18.2% at the same cost per GB-month; what drove the higher use, and is it expected to continue?
5. The dev-sandbox account has 2,700 of Compute in October and none in September; what runs there, and was it planned?

Questions for finance:
1. The dev-sandbox account is new this month in Compute at 2,700; did the October budget expect it?
2. Who should own the 2,700 of unallocated Compute in dev-sandbox?
3. Logging and monitoring, 4,300, is shared and 1,300 over budget; should it be divided between teams, and how?
4. Container registry, 350, is not in the budget; is it a new service or a renamed budget line?

Decisions for people (6):
1. Compute is 6,000 over a budget of 20,000. Choices: accept the variance, change the budget, or ask engineering to look further. The finance lead and the Platform team approve any change in spend.
2. Machine learning training is 1,900 under a budget of 5,000. Choices: accept the variance, change the budget, or ask engineering whether the work will return. The finance lead and the Data team approve any change in spend.
3. Logging and monitoring is 1,300 over a budget of 3,000. Choices: accept the variance, change the budget, or ask engineering to look further. The finance lead and the Platform team approve any change in spend.
4. Object storage is 1,200 over a budget of 4,000. Choices: accept the variance, change the budget, or ask engineering to look further. The finance lead and the Data team approve any change in spend.
5. Unallocated cost is 2,700. Choices: name an owner, or leave it unallocated for now. The finance lead settles it, and the service owner approves any change in spend.
6. Container registry, 350, is not in the budget. Choices: add it to the budget, or confirm it is a renamed line. The finance lead and the Platform team approve any change in spend.

Not supplied or checked: No cloud account was read, no resource was inspected, operational dependencies were not checked and no cause was established. All optional inputs were supplied.

Every figure traces to the billing export for 2026-09 and 2026-10, the budget for 2026-10 and the files supplied. The bridge changes no records, touches no cloud account and sends nothing.
```

What was observed in the second run:

- The bridge added up on the first pass (44,000 + 7,600 = 51,600, equal to the export total) and every figure matches the first run.
- The output is identical to the published example. It was written with the example already read, so the identical wording is not independent confirmation that a fresh assistant would produce it; the first run showed the earlier wording differing in list order and in the wording of some questions.
- Cost per unit is printed with four decimals when under 1 for Compute, Logging and monitoring and Object storage, and with two for Machine learning training (5.00), as the rule says.
- A material service not in the budget, a budgeted service with no export rows and an account that had cost in another service last month are not in the example's inputs, so none of those rules was exercised.
- This was one more run by one model on one invented example. No client data was used and nothing here shows how the template performs on a real billing export.

# Cloud spend variance bridge

Capability template, version 0.1.0.

## Purpose

Turn a cloud or tooling billing export, the month's budget, a cost-owner mapping and usage figures into one bridge from budget to actual for a finance lead and an engineering manager: every service as a step, the large moves explained by what the exports show, the usage beside each, the costs with no owner or shared between owners, and the questions that engineering and finance must answer. The assistant finds no cause on its own. It reads only the files it is given, touches no cloud account, resizes or switches off nothing, and never approves or changes any spend.

## When to use it and when not to

Use it when the monthly cloud or tooling bill lands away from budget, or when a part-month export shows it heading that way. It covers any usage-billed infrastructure or tooling that appears as services in a billing export.

Do not use it:

- to list every subscription from a card statement. Software subscription and vendor spend review does that;
- to write finance's commentary for a budget line across the whole business. Budget versus actual variance commentary does that;
- to group payables by supplier. Supplier spend analysis does that;
- to decide what to resize, switch off or buy. Engineering confirms what each resource is for, and finance and the service owners approve any change in spend;
- to forecast the next month or set the next budget.

## Roles

- **Runs it:** the finance lead or the engineering manager.
- **Answers the engineering questions and confirms what depends on each service:** the engineering manager, or the owner named for the service.
- **Answers the finance questions and settles unallocated and shared costs:** the finance lead.
- **Approves any change in spend:** the finance lead together with the service owner. Always people.
- **Makes any change in a cloud account:** the people the company names, outside this capability.

## Inputs

1. **Settings,** typed by the runner: the company; the month analysed (YYYY-MM); the prior month (YYYY-MM); the currency; the finance lead and the engineering manager; [your amount threshold] (default 1,000 in the currency); [your percent threshold] (default 10%); [your shared tag] (default `shared`). If the month or the currency is missing, stop and ask.
2. **Billing export,** one row per service, account and month, containing the analysed month and, ideally, the prior month, with these default headers: `month` (YYYY-MM), `service`, `account`, `owner_tag`, `cost`. `owner_tag` may be blank. A credit or refund is a negative `cost`. If the analysed month has no rows, stop. If the prior month has no rows, continue and write "prior month not in the export" wherever a prior-month figure would go.
3. **Budget,** one row per service for the analysed month, with these default headers: `service`, `owner`, `budget`. If the budget is annual or for another period, stop and ask for the monthly figure; never divide it. If the budget is missing, stop: there is nothing to bridge.
4. **Cost-owner mapping** (optional), one row per account, with these default headers: `account`, `owner`. If it is missing, write "cost-owner mapping not supplied" under Not supplied or checked, and every row without a tag is unallocated.
5. **Usage figures** (optional), one row per service, with these default headers: `service`, `unit`, `usage_this_period`, `usage_prior_period`. One unit per service. If they are missing, write "usage figures not supplied" and print no usage context.

Headers are matched ignoring case and surrounding spaces. If a required header is not there, stop and ask which column holds that information; never guess and never use another column in its place. Service names, account names and owner names are matched exactly as written, ignoring case and surrounding spaces; two names that differ in any other way are never treated as the same.

The assistant works from files and notes the person supplies. It needs no connection to a cloud account or an accounting system and never asks for a password, a login code, an access key or a token.

## The procedure

1. **Check the inputs.** One currency throughout; every `cost`, `budget` and usage value reads as a number. Each `month` value is the analysed month or the prior month; any other month, stop and ask. Two budget rows for the same service, stop and ask. Two export rows with the same month, service, account and owner_tag, stop and ask whether they are one charge counted twice or two real charges; never drop either on your own.
2. **Service totals.** Add `cost` by service for the analysed month (the actual) and for the prior month. Show whole currency units unless the export carries cents. Add all analysed-month rows: the export total. It must equal the sum of the service totals.
3. **Match to the budget.** A service in the export and the budget is a budgeted service. A service in the budget with no analysed-month rows has an actual of 0 and is listed with "no cost in the export". A service in the export and not in the budget is not in the budget; its variance is its whole actual.
4. **Variance.** For each budgeted service, variance = actual − budget, and variance percent = variance ÷ budget, to one decimal place, with halves rounded up. A positive variance is over budget. The overall result: total budget, total actual, total variance and its percent, and the change from the prior month's total in money and percent.
5. **Material moves.** A budgeted service is material when its variance, ignoring the sign, is at least [your amount threshold] and its variance percent, ignoring the sign, is at least [your percent threshold]. Both tests must be met. A service not in the budget is material when its actual is at least [your amount threshold]; its variance is its whole actual, and it is ordered with the other material moves by that amount. All other services are within the threshold. Order material moves by the size of the variance, largest first, ties in service order. **Service order** means alphabetical by service name, ignoring case, and it orders every other list of services below.
6. **The bridge.** Start at the total budget. Add one step for each material move with its variance, then one step for all budgeted services within the threshold together, then one step for all services not in the budget that are not material, together. A material service not in the budget has its own step among the material moves and is left out of the grouped step; if none is left for the grouped step, print it as (0): 0. The last line is the total actual. Check that budget plus the steps equals the actual, and that the actual equals the export total. If either fails, stop and report the figures and the difference.
7. **Cost owners.** For every analysed-month row, set the cost owner:
   - if `owner_tag` is filled and equals [your shared tag], the row is **shared**;
   - otherwise, if `owner_tag` is filled, the owner is the tag as written;
   - otherwise, if the account is in the mapping, the owner is the mapped owner;
   - otherwise the row is **unallocated**.
   Total the rows by cost owner, largest amount first (ties alphabetical), with shared and unallocated last, and show each owner's share of the actual as a percent to one decimal place (the shares may add to 99.9 or 100.1). Do not divide a shared cost between owners and do not assign an unallocated row to anyone.
8. **Detail for each material move.** Print the budget, actual and variance with its percent (for a material service not in the budget, "not in the budget" in place of the budget, budget owner and percent, and its whole actual as the variance); the prior-month total and the change in money and percent; the budget owner; the actual split by cost owner, each part marked "tag" or "mapping", or "no tag, account not mapped" for unallocated parts; and any account with cost in this service in the analysed month and none in this service in the prior month, marked "new this month" with its amount. An account that had cost in the prior month under a different service is still new in this service; say so in the line ("also had cost in [other service] last month"). If the prior month is not in the export, print the split and "prior month not in the export".
9. **Usage context.** For each material move whose service has usage figures, print the unit, usage in both months and its change in percent; then the cost per unit in both months (the service total divided by the usage, to four decimal places if the result is under 1, otherwise two) and its change in percent. Call usage or unit cost **flat** when it changed by 2% or less in either direction, otherwise **up** or **down**. If either month's usage or prior cost is 0, write "not computed". List every service, material or not, that has no usage row under "No usage figures". Usage is context: state it, and never say it is the cause.
10. **Unallocated and shared costs.** List each unallocated row group (service and account, in service order) with its amount, and the unallocated total with its share of the actual (the same share printed under Costs by cost owner). List shared costs by service, in service order, with the shared total. If there are none, print "None".
11. **Questions.** Write each as one sentence that rests on a fact printed above, addressed to engineering or to finance. Recommend nothing. List them in the order of the rules below, and within a rule in the order of the material moves, then service order, then account.
    - **For each material move with usage figures:** if usage is up and cost per unit is flat, ask engineering what drove the higher use and whether it is expected to continue; if usage is flat and cost per unit is up, ask engineering what else changed in how the service is run or billed; if both are up, ask both; if usage is down, ask engineering whether the lower use is lasting or a timing effect; if usage is flat and cost per unit is flat, ask engineering to explain the movement from their own knowledge of the service.
    - **For each material move without usage figures:** ask engineering for a usage measure for the service.
    - **For each account marked "new this month":** ask engineering what runs there and whether it was planned, and ask finance whether the budget expected it.
    - **For the unallocated total:** ask finance who should own it.
    - **For each shared cost that is material:** ask finance whether and how it should be divided; the capability divides nothing.
    - **For each service not in the budget:** ask finance whether it is a new service or a renamed budget line.
12. **Decisions.** One numbered decision for each material move (a material service not in the budget has one decision, as a material move, and not a second), for the unallocated total when it is above 0, and for each other service not in the budget. Each states the facts and the choices open to the people named, such as accepting the variance, changing the budget, or asking engineering to look further. Name the finance lead and the service owner as the people who approve any change in spend. For the unallocated total, name the finance lead as the person who settles it (see Roles), with the service owner approving any change in spend. The assistant makes no choice.
13. **Not supplied or checked.** Always say that no cloud account was read, that no resource was inspected, that operational dependencies were not checked, and that causes were not established. Add every optional input that was not supplied.
14. **Trace line and return.** Name the export months, the budget month and the files behind every figure. Return the draft to the person who ran it, for the finance lead and the engineering manager. Nothing is sent from here.

## Exceptions and stop conditions

- **A required header does not match:** stop and ask which column holds that information.
- **The budget is not for one month:** stop and ask for the monthly figure.
- **A month in the export is neither the analysed month nor the prior month:** stop and ask.
- **The bridge or the export total does not add up:** stop and report the figures and the difference.
- **Duplicate rows or two budget rows for one service:** stop and ask.
- **A service name differs from a budget name only in spelling:** treat it as a different service, list it under not in the budget and ask whether it is a renamed line.
- **Prior month missing:** continue without prior-month figures, say so, and skip the "new this month" test.
- **Asked to say why costs rose, to resize or switch off a resource, to approve a spend change, to divide a shared cost or to assign an unallocated one:** decline and put the question to the right person.

## Output format

```
CLOUD SPEND VARIANCE BRIDGE: [month]

For: [finance lead] and [engineering manager]. Currency [currency]. Budget for [month]; billing export for [month] and [prior month]. A move is material at [amount threshold] and [percent threshold] or more.

Result: Budget [total]. Actual [total]. Variance [+/-amount] ([percent]%). Prior month [total], so the month [rose/fell] [amount] ([percent]%).

Bridge:
Budget [total]
[Service] ([budget owner]): [+/-variance]
[Material service not in the budget] (not in the budget): [+/-variance]
Budgeted services within the threshold ([n]): [+/-variance]
Services not in the budget ([n]): [+/-variance]
Actual [total]
Check: [budget] + [steps] = [actual]; export rows total [export total].

Material moves ([n]):
1. [Service] (budget owner [owner]): budget [b], actual [a], variance [+/-v] ([p]%). [A material service not in the budget reads: [Service] (not in the budget): actual [a], variance [+a].] Prior month [pm]; change [+/-d] ([q]%). Cost owners: [owner amount (tag or mapping)]; [unallocated amount (no tag, account not mapped)]. New this month: [account amount, or None]. Usage: [unit], [prior] to [this] ([change]%, [flat/up/down]); cost per unit [prior] to [this] ([change]%, [flat/up/down]).

Within the threshold, in service order: [service, variance]; [service, variance]. Or None.

Not in the budget, in service order: [service, actual, cost owner]. Or None.

Costs by cost owner: [owner amount (share%)]; ... Shared [amount (share%)]. Unallocated [amount (share%)].

Shared costs: [service, amount]. Total [amount]. Or None.

Unallocated costs: [service, account, amount]. Total [amount] ([share]% of the actual). Or None.

No usage figures, in service order: [services]. Or None.

Questions for engineering:
1. [Question that rests on a printed fact.]
Or None.

Questions for finance:
1. [Question that rests on a printed fact.]
Or None.

Decisions for people ([n]):
1. [Facts and choices. Approved by the finance lead and the service owner if spend changes.]
Or None.

Not supplied or checked: No cloud account was read, no resource was inspected, operational dependencies were not checked and no cause was established. [Each optional input not supplied.]

Every figure traces to the billing export for [months], the budget for [month] and the files supplied. The bridge changes no records, touches no cloud account and sends nothing.
```

## Reviewer checklist

1. The bridge adds up: budget plus the steps equals the actual, and the actual equals the export total. (Finance lead)
2. Every service's actual and budget match the files supplied. (Finance lead)
3. The material moves meet both thresholds, and no service that meets both is hidden in the within-threshold step. (Finance lead)
4. Every cost owner comes from a tag or the mapping; nothing unallocated has been assigned and no shared cost divided. (Finance lead)
5. The usage and cost-per-unit figures match the usage rows, and no sentence calls usage the cause. (Engineering manager)
6. Each question rests on a printed fact and goes to the right side. (Engineering manager and finance lead)
7. The decisions name the people who approve a spend change, and the assistant has made none. (Finance lead)

## Acceptance tests

Proposed tests. None has been run as a test. Test 1 has the same shape as the invented example in the public example, which was tried once; the record is `public/trial.md`.

1. **Normal month.** Budget 44,000 and actual 51,600 across eight services. Expected: the bridge adds up and every section is printed.
2. **Both thresholds.** A service over by 250 on a budget of 2,500 (10.0%), with an amount threshold of 1,000. Expected: within the threshold.
3. **Header mismatch.** The export has `spend` instead of `cost`. Expected: stops and asks which column holds the cost.
4. **Annual budget.** The budget file gives annual figures. Expected: stops and asks for the monthly figure.
5. **Unallocated row.** A row with no tag in an account missing from the mapping. Expected: listed as unallocated, with a question to finance and no owner assigned.
6. **Shared cost.** A row tagged with the shared tag. Expected: listed as shared and left undivided.
7. **Prior month missing.** Expected: continues, says "prior month not in the export" and skips new-this-month.
8. **Asked for a cause.** "Why did compute rise?" Expected: declines, states usage and cost per unit, and puts the question to engineering.
9. **Asked to resize.** Expected: declines; changes in spend are approved by the finance lead and the service owner.
10. **Duplicate rows.** Two identical export rows. Expected: stops and asks.

## Instructions for the AI assistant

```
You prepare the cloud spend variance bridge for a finance lead and an
engineering manager. You read only the files and notes the user supplies.
You never touch a cloud account, resize or switch off anything, approve or
change any spend, send anything or edit any record. People decide.

The user will supply: the settings (month, prior month, currency, the two
people, thresholds); a billing export with headers month, service,
account, owner_tag, cost; the month's budget with headers service, owner,
budget; optionally an account-to-owner mapping with headers account, owner;
optionally usage rows with headers service, unit, usage_this_period,
usage_prior_period. If a required header does not match, stop and ask
which column holds it. If the budget is not for one month, stop and ask
for the monthly figure. If the month or the currency is missing, or the
budget is missing, stop. If duplicate rows or any other month appear, stop
and ask. If the prior month is not in the export, continue, write "prior
month not in the export" where its figures would go, and skip the "new this
month" test. Never ask for a password, login code, access key or token.

1. Total cost by service for the month and the prior month. The export
   total must equal the sum of the services.
2. Variance = actual - budget for each budgeted service, with the percent
   of budget, to one decimal place, halves rounded up. A service not in the
   budget has its whole actual as variance. A budgeted service with no
   rows in the month has an actual of 0 and is listed with "no cost in the
   export".
3. A move is material when the variance and the percent both reach the
   thresholds, ignoring the sign (a service not in the budget: the amount
   only), and then it gets its own step and one decision like any material
   move and is left out of the grouped step for services not in the budget.
   Name matching is exact apart from case and surrounding spaces.
   "Service order" means alphabetical by service name, ignoring case.
4. Build the bridge: budget, one step per material move (largest variance
   first, ties in service order), one step for the rest of the budgeted
   services, one for the other services not in the budget, then the
   actual. Check it adds up. If it does not, stop and report the figures.
5. Set each row's cost owner: the shared tag means shared; any other tag
   is the owner; otherwise the mapping; otherwise unallocated. Never
   divide shared costs and never assign unallocated ones.
   Order cost owners largest first, ties alphabetical, shared and
   unallocated last.
6. For each material move print the split by owner, the prior-month change,
   accounts new this month (cost in this service now, none in this service
   last month; if the account had cost in another service last month, say
   "also had cost in [that service] last month"), and the usage context:
   usage and cost per unit in both months. Cost per unit is the service total divided by usage, to four
   decimal places if under 1, otherwise two; say "not computed" if a usage
   figure or the prior cost is 0. Call usage or unit cost flat when it
   changed by 2% or less in either direction, otherwise up or down. Usage
   is context, never the cause. List within-threshold services, services
   not in the budget, shared and unallocated costs and services with no
   usage figures in service order.
7. Write questions for engineering and for finance, each resting on a
   printed fact, in this order: material moves first, then new accounts,
   the unallocated total, material shared costs and services not in the
   budget. For a material move with usage figures: usage up and unit cost
   flat, ask engineering what drove the higher use and whether it will
   continue; usage flat and unit cost up, what else changed in how the
   service is run or billed; both up, ask both; usage down, whether the
   lower use is lasting or timing; both flat, ask engineering to explain
   the movement from their knowledge of the service. Without usage
   figures, ask engineering for a usage measure. For a new account, ask
   engineering what runs there and whether it was planned, and finance
   whether the budget expected it. For the unallocated total, ask finance
   who should own it. For a material shared cost, ask finance whether and
   how to divide it. For a service not in the budget, ask finance whether
   it is new or a renamed line. Recommend nothing. Write one decision
   for each material move, the unallocated total and each other service not
   in the budget (a material service not in the budget has one decision,
   not two), naming the finance lead and the service owner as the
   approvers of any spend change; for the unallocated total the finance
   lead settles it.
8. Say that no cloud account was read, no resource was inspected,
   dependencies were not checked and no cause was established.
9. Use the output format exactly. Print "None" for an empty section.

If asked for a cause, to resize or switch off a resource, to approve a
change, or to fix a figure so it adds up, decline and name the person who
decides.
```

## What to customize

- The amount and percent thresholds, and the tolerance for calling a figure flat.
- Your shared tag, and who owns costs that have none.
- The usage measure you trust for each service.
- The monthly budget layout and the people who approve a change.
- Which exports the assistant may read in ChatGPT, Claude, Copilot or Gemini.

## Version notes

- 0.1.0, 10 November 2026. Written by Fully Powered AI. Not yet tested in a client environment.

---
name: "cloud-spend-variance-bridge"
description: "Turn a cloud or tooling billing export, the month's budget, a cost-owner mapping and usage figures into one bridge from budget to actual for a finance lead and an engineering manager: every service as a step, the large moves explained by what the exports show, the usage beside each, the costs with no owner or shared between owners, and the questions that engineering and finance must answer. The assistant finds no cause on its own. It reads only the files it is given, touches no cloud account, resizes or switches off nothing, and never approves or changes any spend."
license: "MIT"
metadata:
  version: "0.1.0"
  publisher: "Fully Powered AI"
  capability: "Cloud spend variance bridge"
---

# Cloud spend variance bridge

This is the technical file for a Fully Powered capability template. It carries the instructions an AI product follows. The complete template, with roles, inputs, exceptions, the reviewer checklist, acceptance tests and what to customize, is in [TEMPLATE.md](TEMPLATE.md). A worked example with invented data is in [EXAMPLE.md](EXAMPLE.md).

## Instructions

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

## Before relying on it

Decide every item under "What to customize" in TEMPLATE.md and set the limits the instructions in this file leave open, written in square brackets such as [N], to your own. Then run the acceptance tests in TEMPLATE.md on past work. A person starts this work, supplies the inputs and decides what happens with the result.

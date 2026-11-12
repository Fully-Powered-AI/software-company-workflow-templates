# Cloud spend variance bridge: an invented example

*Illustrative example with invented data.* The company, the teams, the accounts, the services, the amounts and the dates below are all invented. Software Company Q is an invented software company. Its finance lead and engineering manager are looking at October's cloud bill, which came in above budget. First come the inputs they supplied, in full, then the bridge the workflow template returned.

## The inputs

### 1. Settings (typed by the finance lead)

```
Company: Software Company Q
Month: 2026-10
Prior month: 2026-09
Currency: USD
Finance lead: Finance lead
Engineering manager: Engineering manager
Amount threshold: 1,000
Percent threshold: 10%
Shared tag: shared
```

### 2. Billing export (both months, one row per service and account)

```
month,service,account,owner_tag,cost
2026-09,Compute,prod-main,Platform team,18800
2026-09,Compute,data-lake,,2700
2026-09,Object storage,data-lake,Data team,3900
2026-09,Object storage,prod-main,,500
2026-09,Managed database,prod-main,Platform team,8100
2026-09,Data transfer,prod-main,,2000
2026-09,Data transfer,data-lake,,600
2026-09,Logging and monitoring,shared-tools,shared,3800
2026-09,Support plan,shared-tools,shared,1500
2026-09,Machine learning training,data-lake,Data team,4800
2026-09,Container registry,prod-main,Platform team,330
2026-10,Compute,prod-main,Platform team,19400
2026-10,Compute,data-lake,,3900
2026-10,Compute,dev-sandbox,,2700
2026-10,Object storage,data-lake,Data team,4600
2026-10,Object storage,prod-main,,600
2026-10,Managed database,prod-main,Platform team,8400
2026-10,Data transfer,prod-main,,2100
2026-10,Data transfer,data-lake,,650
2026-10,Logging and monitoring,shared-tools,shared,4300
2026-10,Support plan,shared-tools,shared,1500
2026-10,Machine learning training,data-lake,Data team,3100
2026-10,Container registry,prod-main,Platform team,350
```

### 3. Budget for 2026-10

```
service,owner,budget
Compute,Platform team,20000
Object storage,Data team,4000
Managed database,Platform team,8000
Data transfer,Platform team,2500
Logging and monitoring,Platform team,3000
Support plan,Finance lead,1500
Machine learning training,Data team,5000
```

### 4. Cost-owner mapping

```
account,owner
prod-main,Platform team
data-lake,Data team
```

### 5. Usage figures

```
service,unit,usage_this_period,usage_prior_period
Compute,vCPU-hours,312000,310000
Object storage,GB-months,52000,44000
Data transfer,GB out,27500,26000
Logging and monitoring,GB ingested,8600,7600
Machine learning training,GPU-hours,620,960
```

## The bridge

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

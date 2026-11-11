# Subscription billing exception sheet: an invented example

*Illustrative example with invented data.* The company, its customers, the plans, the prices, the dates and the amounts below are all invented. The company is an invented software company, called "the Company" here, whose billing specialist runs the monthly subscription invoices and whose finance lead approves corrections. Customers are lettered. First come the inputs the billing specialist supplied, in full, then the sheet the capability returned.

## The inputs

### 1. Settings

```
Run: November 2026 monthly run (draft lines reference DRAFT-1130)
Billing period: 2026-11-01 to 2026-11-30 (30 days)
Currency: USD
Tolerance: 0.00 on price, quantity and arithmetic
Seat basis: the seats on record at the start of the period
Mid-period change rule: not supplied
Usage measures: seats are recorded as "seats"; P-API and the API calls inside B-TEAM are recorded as "api_calls_thousands" (one record unit is 1000 calls)
Verifies exceptions: billing specialist
Approves corrections, credits and revised invoices: finance lead
```

### 2. Subscription export

```
account_id,account_name,plan_code,quantity,term_start,term_end,billing_cycle,status
A-101,Customer A,P-PRO,12,2026-02-01,2027-01-31,monthly,active
A-102,Customer B,P-STD,40,2026-03-01,2027-02-28,monthly,active
A-103,Customer C,P-PRO,8,2026-01-01,2026-12-31,monthly,active
A-103,Customer C,P-API,,2026-01-01,2026-12-31,monthly,active
A-104,Customer D,B-TEAM,1,2026-04-01,2027-03-31,monthly,active
A-105,Customer E,P-STD,25,2026-03-01,2027-02-28,monthly,active
A-106,Customer F,P-PRO,15,2026-05-01,2027-04-30,monthly,active
A-107,Customer G,P-STD,10,2026-05-01,2027-04-30,monthly,active
A-108,Customer H Europe,P-STD,20,2026-06-01,2027-05-31,monthly,active
A-109,Customer H North America,P-STD,12,2026-06-01,2027-05-31,monthly,active
A-110,Customer J,P-STD,5,2026-04-01,2026-09-30,monthly,cancelled
```

### 3. Approved price mapping

```
plan_code,plan_name,billing_unit,unit_price,currency,billing_cycle,includes,effective_from
P-STD,Standard seat,seat,25.00,USD,monthly,,2026-01-01
P-PRO,Pro seat,seat,45.00,USD,monthly,,2026-01-01
P-API,API calls,1000 calls,8.00,USD,monthly,,2026-01-01
B-TEAM,Team bundle,bundle,520.00,USD,monthly,10 P-PRO seats and 50 thousand API calls,2026-01-01
```

### 4. Seat and usage records

```
account_id,measure,period_start,period_end,quantity
A-101,seats,2026-02-01,2027-01-31,12
A-102,seats,2026-03-01,2027-02-28,40
A-103,seats,2026-01-01,2026-10-31,10
A-103,seats,2026-11-01,2026-12-31,8
A-103,api_calls_thousands,2026-11-01,2026-11-30,120
A-104,seats,2026-04-01,2027-03-31,10
A-104,api_calls_thousands,2026-11-01,2026-11-30,62
A-105,seats,2026-03-01,2027-02-28,25
A-106,seats,2026-05-01,2026-11-14,15
A-106,seats,2026-11-15,2027-04-30,18
A-107,seats,2026-05-01,2027-04-30,10
A-108,seats,2026-06-01,2027-05-31,20
A-109,seats,2026-06-01,2027-05-31,12
```

### 5. Draft invoice lines (DRAFT-1130)

```
line,account_id,account_name,plan_code,quantity,unit_price,amount,period_start,period_end
1,A-101,Customer A,P-PRO,12,45.00,540.00,2026-11-01,2026-11-30
2,A-102,Customer B,P-STD,40,25.00,1000.00,2026-11-01,2026-11-30
3,A-103,Customer C,P-PRO,10,45.00,450.00,2026-11-01,2026-11-30
4,A-103,Customer C,P-API,120,8.00,960.00,2026-11-01,2026-11-30
5,A-104,Customer D,B-TEAM,1,520.00,520.00,2026-11-01,2026-11-30
6,A-105,Customer E,P-STD,25,28.00,700.00,2026-11-01,2026-11-30
7,A-106,Customer F,P-PRO,15,45.00,675.00,2026-11-01,2026-11-30
8,,Customer H,P-STD,20,25.00,500.00,2026-11-01,2026-11-30
9,A-110,Customer J,P-STD,5,25.00,125.00,2026-11-01,2026-11-30
```

### 6. Amendments and credits

```
account_id,date,type,detail,amount
A-102,2026-11-03,credit,Goodwill credit approved by the finance lead for the November invoice,-100.00
A-103,2026-10-28,amendment,Seats reduced from 10 to 8 from 2026-11-01,
```

## The sheet

**BILLING EXCEPTION SHEET: November 2026 monthly run (DRAFT-1130)**

**For:** Billing specialist, to verify; finance lead, to approve. Period 2026-11-01 to 2026-11-30. Prepared from the six inputs above.

**Inputs read:** 11 subscription rows, 4 price-mapping rows, 13 seat or usage rows, 9 draft invoice lines totalling \$5,470.00, 2 amendments or credits. Headers matched: yes.

**Result:** 2 lines clean (\$1,500.00). 4 lines with a difference computed (\$2,275.00 invoiced), of which 1 with a credit not on the draft. 3 lines held open (\$1,695.00 invoiced). 1 subscription not billed. Check: \$1,500.00 + \$2,275.00 + \$1,695.00 = \$5,470.00, the draft total.

**Differences computed:**
- E1, line 3, A-103 Customer C, P-PRO. Kind: quantity. Invoiced 10 seats at \$45.00 = \$450.00. Records show 8 seats from 2026-11-01; the amendment of 2026-10-28 reduces seats from 10 to 8 from that date. Expected 8 × \$45.00 = \$360.00. Invoiced above expected by \$90.00.
- E2, line 6, A-105 Customer E, P-STD. Kind: price. Invoiced 25 seats at \$28.00 = \$700.00. The mapping price is \$25.00, so expected 25 × \$25.00 = \$625.00. Invoiced above expected by \$75.00. No amendment on file for this account.
- E3, line 9, A-110 Customer J, P-STD. Kind: billed outside the term. Invoiced 5 seats at \$25.00 = \$125.00. The subscription is cancelled and its term ended 2026-09-30. No seat record covers November. Expected \$0.00. Invoiced above expected by \$125.00.
- E4, line 2, A-102 Customer B, P-STD. Kind: credit not on the draft. Invoiced 40 seats at \$25.00 = \$1,000.00, which agrees with the mapping and the seat records. The approved credit of -\$100.00 dated 2026-11-03 has no credit line on the draft. Expected net \$1,000.00 - \$100.00 = \$900.00. Draft above expected by \$100.00.

**Held open, nothing computed:**
- E5, line 5, A-104 Customer D, B-TEAM. Kind: bundled line. The bundle price agrees with the mapping (1 × \$520.00 = \$520.00). The bundle includes 10 Pro seats and 50 thousand API calls. Records show 10 seats, which agrees, and 62 thousand API calls, which is 12 thousand above the included amount. The line's quantity of 1 is not compared with the 10 seats on record; the bundle step governs it. The mapping does not say whether calls above the included amount are charged, so no expected amount is computed.
- E6, line 7, A-106 Customer F, P-PRO. Kind: mid-period change. Records show 15 seats to 2026-11-14 and 18 seats from 2026-11-15. The draft bills 15 seats × \$45.00 = \$675.00, which equals the seats at the start of the period. No mid-period change rule was supplied, so no expected amount is computed.
- E7, line 8, no account_id, "Customer H", P-STD, 20 × \$25.00 = \$500.00. Kind: ambiguous account. Candidates: A-108 Customer H Europe (P-STD, 20 seats) and A-109 Customer H North America (P-STD, 12 seats). The name matches neither exactly. The quantity of 20 agrees with A-108 only, which is not treated as a match. Both subscriptions stay with this item.

**Not billed:**
- E8, A-107 Customer G, P-STD, active, 10 seats on record for the whole period, no draft line. Expected 10 × \$25.00 = \$250.00 not on the draft.

**Credits and amendments:**
- A-102, 2026-11-03, credit of -\$100.00: linked to line 2; no credit line on the draft (E4).
- A-103, 2026-10-28, amendment, seats from 10 to 8 from 2026-11-01: explains the records behind E1; line 3 still bills 10.

**Clean lines:** 1 (A-101, 12 × \$45.00 = \$540.00 against 12 seats on record), 4 (A-103 P-API, 120 × \$8.00 = \$960.00 against 120 thousand calls on record).

**Could not be assessed:** The cost of the 12 thousand calls above the bundle allowance in E5. The charge for the change of seats in E6. Which Customer H subscription line 8 belongs to. Nothing else was left unchecked.

**Questions for the billing specialist:**
1. E1: confirm that line 3 still bills 10 seats against the amendment of 2026-10-28 and the seat record from 2026-11-01.
2. E2: confirm whether Customer E has any price agreement that is not in the amendments file.
3. E3: confirm that A-110 should not be billed and why a November line exists.
4. E4: check the credit record for A-102 dated 2026-11-03 and ask why no credit line is on the draft.
5. E5: ask whether calls above the bundle allowance are charged, and at what price.
6. E6: ask for the Company's rule for seats added in the middle of a period.
7. E7: find which Customer H account the line is for.
8. E8: confirm whether A-107 was left off the run on purpose.

**Decisions for finance:** 4.
1. Whether to correct lines 3, 6 and 9 as E1 to E3 describe, or to leave any as invoiced.
2. Whether the \$100.00 credit in E4 is applied to this run.
3. Whether A-107 is added to this run or to the next (E8).
4. How the open items E5 to E7 are billed once the specialist has the answers.

Every figure traces to the six inputs above. The sheet issues and changes no invoice and sends nothing.

# Subscription billing exception sheet: trial on the invented example

- **Product:** Claude, run in Claude Code
- **Model:** Claude Sonnet 5.5 (model ID claude-sonnet-5-5)
- **Date:** 2026-11-10
- **Template version:** 0.1.0

This is a record of one run of the capability template on its own invented example. The company, customers, plans and amounts are invented and no client data was used. It is not a test in any company's environment.

The inputs were the invented example in `public/example.md` (the six inputs under "The inputs"). No client data was used. The instruction block and output format from `member/template.md` were followed. The assistant did not read the example's sheet until its own sheet was finished. It then compared the two.

## What came out

The sheet below is the substance of the output.

**BILLING EXCEPTION SHEET: November 2026 monthly run (DRAFT-1130)**

Inputs read: 11 subscription rows, 4 price-mapping rows, 13 seat or usage rows, 9 invoice lines totalling $5,470.00, 2 amendments or credits. Headers matched: yes.

Result: 2 lines clean ($1,500.00). 4 lines with a difference computed ($2,275.00 invoiced). 3 lines held open ($1,695.00 invoiced). 1 subscription not billed. 1 credit not on the draft. Check: $1,500.00 + $2,275.00 + $1,695.00 = $5,470.00.

Differences computed:
- E1, line 2, A-102 Customer B, P-STD. Credit not on the draft. Invoiced 40 x $25.00 = $1,000.00, agreeing with the mapping and the records. A credit of -$100.00 dated 2026-11-03 has no credit line on the draft. Expected net $900.00. Draft above expected by $100.00.
- E2, line 3, A-103 Customer C, P-PRO. Quantity. Invoiced 10 x $45.00 = $450.00. The seat record covering 2026-11-01 shows 8. The amendment of 2026-10-28 is cited. Expected $360.00. Above by $90.00.
- E3, line 6, A-105 Customer E, P-STD. Price. Invoiced 25 x $28.00 = $700.00. Mapped price $25.00. Expected $625.00. Above by $75.00.
- E4, line 9, A-110 Customer J, P-STD. Billed outside the term. The subscription is cancelled and its term ended 2026-09-30. Expected $0.00. Above by $125.00.

Held open, nothing computed:
- E5, line 5, A-104 Customer D, B-TEAM. Bundled line. The bundle price agrees with the mapping. Seats on record (10) are within the included 10. API calls on record (62 thousand) are above the included 50 thousand, and the mapping does not say how the excess is charged.
- E6, line 7, A-106 Customer F, P-PRO. Mid-period change. 15 seats to 2026-11-14, then 18 from 2026-11-15. The line bills 15. No rule was supplied.
- E7, line 8, no account_id, "Customer H", P-STD, 20 x $25.00 = $500.00. Ambiguous account. Candidates: A-108 Customer H Europe (P-STD, 20) and A-109 Customer H North America (P-STD, 12). Neither name is identical to "Customer H". The matching quantity of 20 is evidence only, not a basis for choosing.

Not billed:
- E8, A-107 Customer G, P-STD, active, 10 seats on record, expected 10 x $25.00 = $250.00.

Credits and amendments: A-102 credit of -$100.00 links to line 2 (E1). A-103 amendment (seats 10 to 8 from 2026-11-01) links to line 3 (E2).

Clean lines: 1 (A-101) and 4 (A-103 P-API, 120 x $8.00 = $960.00 against 120 thousand calls on record).

Could not be assessed: the cost of the 12 thousand calls above the bundle allowance; the charge for the seat change on line 7; which Customer H subscription line 8 belongs to.

Questions for the billing specialist (one per item, each naming the record to look at) and four decisions for finance followed. The summary written at the time named three of them (correct or leave lines 2, 3, 6 and 9; add A-107 to this run or the next; how the open items are billed); the fourth was not recorded. The sheet ended with the trace line: every figure traces to the six inputs, and the sheet issues and changes no invoice and sends nothing.

## What was observed

- Every required part of the output format was produced, and the groups added up to the invoice total.
- No stop condition was triggered: headers matched, nothing was missing, and no mapping rows overlapped.
- Differences from the example as it stood at the run (the example has since been changed, see below):
  - The example lists line 2 as clean and reports the unapplied credit as a separate item (its E4). This run put line 2 in the "difference computed" group, because step 11 of the template calls a credit not on the draft a difference of that kind. So this run shows 2 clean lines ($1,500.00) and 4 computed ($2,275.00); the example shows 3 clean ($2,500.00) and 3 computed ($1,275.00). The totals and the open group agree. The template does not say which grouping is right.
  - The example's E-numbers run in a different order, and its wording differs. The figures and kinds agree item for item.
- Facts in the example's sheet that are not in the inputs: "the draft was not updated" (inferred from the amendment and the invoiced quantity) and "no amendment on file for this account" for Customer E (true of the file, but a statement about absence). Nothing in this run's output was outside the inputs.
- Places where the instructions were ambiguous and a guess was needed:
  - Which group a line belongs to when its own arithmetic and records are right but a credit is missing (see above).
  - Whether the quantity check applies to a bundle line. The bundle line bills 1 unit while the seat records show 10. This run treated the bundle step as governing and skipped the seat-quantity check.
  - How a usage measure such as `api_calls_thousands` maps to a plan whose billing unit is "1000 calls". There is no stated link between a plan and its measure name; this run inferred it.
  - The "Result" line asks for a count of lines with a difference, but a credit not on the draft is counted both as a line and as a separate figure.
- The template's acceptance tests are marked as proposed and not yet run; this trial covered the invented example only, not each test.

## What was changed after the run, and not run again

Changed on 10 November 2026 after an independent review, and not run again. The output and the observations above are as recorded and describe the template and the example as they stood at the run:

- **Credit not on the draft.** The procedure, the instruction block and the output format now say that a line whose own figures are right but whose credit is missing goes in the "difference computed" group, never "clean", at its invoiced amount. The item is set out with the invoiced figures, the credit, the expected net and the amount the draft is above it. The Result line no longer counts such a credit as a figure of its own; it says "of which [n] with a credit not on the draft". The example now matches the grouping this run produced: 2 clean ($1,500.00), 4 computed ($2,275.00), 3 held open ($1,695.00).
- **Bundle quantity.** Step 6 of the procedure and of the instruction block now says a bundle line skips the quantity check and step 8 governs it, as this run did.
- **Usage measure names.** The settings now name the measure each usage plan and each bundled usage amount is recorded under, and the assistant stops and asks if one is missing instead of inferring it. The example's settings gained one line giving the names. The usage-record rule now also accepts records whose spans together cover the period exactly.
- **Instruction block and wording, 10 November 2026, after the independent review.** The numbered steps of the instruction block now match the procedure (1 to 14). The block now also carries the rules that were only in the procedure or the stop conditions (comparing names ignoring case, spaces and punctuation; "no record" for a usage plan; a duplicate's expected amount; currency mismatch; two mapping rows for one date; unlinked amendments), the expected headers inline, and a definition of a candidate for an ambiguous account (an export name that contains the line's name or is contained in it). The opening line of the block no longer says the company is a software company. None of this alters the output format or the example's inputs, and none of it has been run.
- **The example.** E4 now has its own question, and "the draft was not updated" now reads "line 3 still bills 10". Wording in step 4 of the procedure was made clearer.

The two changes to the settings and to step 6 for usage records alter what the assistant is told, so the template as it now stands has not been run end to end. The first of the guesses listed above (the group for a line with a missing credit) and the second (the bundle quantity check) are settled in the instructions; the third (the measure name) is settled by the settings line; the fourth (the Result count) by the new Result wording. None of these has been confirmed by a second run.

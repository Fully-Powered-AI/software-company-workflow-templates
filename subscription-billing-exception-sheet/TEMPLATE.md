# Subscription billing exception sheet

Workflow template, version 0.1.0.

## Purpose

Prepare the sheet a billing specialist works from before a subscription billing run or when a customer disputes a charge. It ties each account's plan, quantity and invoice lines to the approved price mapping and to the seat or usage records, shows each difference with the amounts behind it, and keeps every doubtful item open: ambiguous account matches, mid-period changes and bundled lines. The assistant prepares and checks. It issues and changes no invoice, applies no credit and takes no accounting or tax position. The billing specialist verifies every exception, and the finance lead approves any correction, credit or revised invoice.

## When to use it and when not to

Use it when the draft invoice lines for a run are ready, before they are issued, or when a customer questions a charge on an issued invoice and the account needs tracing. In the dispute case, give it the disputed invoice, the customer's description of what is wrong, and the records for that one account.

Do not use it to match payments to invoices (use the receivables exception review), to tie a payment processor's payouts to the bank, to check bills the company owes, to decide how revenue is recognised, or to decide tax. Do not use it if there is no approved price mapping: without one there is nothing to check a price against.

## Roles

- **Runs it:** the billing specialist or the revenue operations lead.
- **Verifies each exception:** the billing specialist, against the source records.
- **Approves corrections, credits and revised invoices:** the finance lead.
- **Supplies the explanation for an open item:** the account owner in customer success or sales, when the billing specialist asks.

## Inputs

Read each file as supplied. Default column headers are listed. If a header does not match, do not guess which column is meant: stop, list the headers found against the headers expected, and ask the billing specialist which is which.

1. **Settings.** Billing period (start and end dates), currency, tolerance (default 0.00), seat basis (default: the quantity on record at the start of the period), the company's rule for a quantity that changes in the middle of a period (default: none, so every such change is held open), the usage measure name that each usage plan, and each usage amount inside a bundle, is recorded under (for example `P-API` and the API calls in `B-TEAM` are recorded as `api_calls_thousands`, in thousands of calls, matching the billing unit "1000 calls"; seats are recorded as `seats`), who verifies, who approves, and the approval threshold if there is one. If the period or currency is missing, stop and ask. If a usage plan or a bundle's usage amount has no measure name, stop and ask; never infer one from the plan name or the billing unit.
2. **Subscription export.** Default headers: `account_id, account_name, plan_code, quantity, term_start, term_end, billing_cycle, status`. One row per account and plan. A usage plan may have a blank quantity.
3. **Approved price mapping.** Default headers: `plan_code, plan_name, billing_unit, unit_price, currency, billing_cycle, includes, effective_from`. `includes` is filled only for a bundle and says what the bundle contains. If missing, stop.
4. **Seat and usage records.** Default headers: `account_id, measure, period_start, period_end, quantity`. One row for each span over which a quantity applied. The measure is `seats` or the name of the usage unit. If missing, stop: no quantity can be checked.
5. **Invoice lines.** Default headers: `line, account_id, account_name, plan_code, quantity, unit_price, amount, period_start, period_end`. These are the draft lines for the run, or the lines of the disputed invoice. If missing, stop. Add a reference for the run or invoice; if absent, ask for one.
6. **Amendments and credits.** Default headers: `account_id, date, type, detail, amount`. If missing, write "amendments and credits not supplied" in that section and continue.

## The procedure

1. **Check the files.** Compare each file's headers with the defaults. Count the rows read in each file. Confirm every invoice line's period lies inside the billing period in the settings; a line with another period is held open as its own item. Stop on any header mismatch.
2. **Arithmetic.** For each line, quantity × unit price must equal the amount, rounded to the cent. A line that does not is a difference of kind "arithmetic".
3. **Match each line to an account.** Use `account_id` when the line has one and the subscription export contains it. If the id is blank or unknown, compare the account name with the export names after ignoring case, spaces and punctuation. If exactly one name is identical, use it and say that the name was the basis. If none or more than one is identical, or the name is only similar, the line is an ambiguous account: list the candidates with their plan and quantity and hold the line open. A matching quantity or amount is evidence to report, never a basis for choosing. Subscriptions named as candidates for an ambiguous line are not also listed as not billed.
4. **Check the plan.** The line's plan code must exist in the price mapping and must be on the matched account in the subscription export. A line billing a plan the account does not hold, or one whose status is cancelled, or whose term ended before the period starts or starts after it, is a difference of kind "billed outside the term". The expected amount is zero.
5. **Check the price.** The line's unit price must equal the mapped unit price within the tolerance, using the mapping row in force on the period start date. A difference is of kind "price": expected amount is invoiced quantity × mapped price.
6. **Check the quantity.** A bundle line skips this step: its quantity is not compared with the seat or usage records, and step 8 governs it. For a seat plan, find the records for the account with measure `seats` whose span includes the period start date. That quantity, under the seat basis, is the expected quantity. For a usage plan, use the records under the measure name the settings give for that plan: a record whose span equals the billing period, or records whose spans together cover the period exactly, with no gap and no overlap, in which case the expected quantity is their sum. A line whose quantity differs is of kind "quantity": expected amount is expected quantity × the mapped price. If no record covers the period, the line is held open as "no record" and no amount is computed.
7. **Mid-period changes.** If the account's records show a second quantity starting after the period start and on or before the period end, the line is held open as "mid-period change". Show both quantities with their dates and the quantity the line bills. If the settings give a rule, say what the rule would produce as a separate sentence, labelled as the rule's result and not as a verified amount. If no rule was supplied, compute nothing.
8. **Bundled lines.** A line for a plan whose mapping row has `includes` filled is a bundle. Check the price of the bundle as a whole against the mapping. Then compare the records for the account with what the bundle includes. If every measure is within the included amount, the line is clean. If a measure is above it, or the mapping does not say how the excess is charged, hold the line open as "bundled line" and compute nothing for the excess. Never split a bundle's price across its parts.
9. **Not billed.** For each subscription row that is active, whose term covers the period and that has records for the period, and that has no matching invoice line (apart from the candidates in step 3): expected amount is the recorded quantity × mapped price; list it as "not billed". A usage plan with no usage record for the period is listed as "no record", with no amount.
10. **Duplicates.** Two lines for the same account, plan and period are a difference of kind "duplicate". The second is the one queried; the expected amount for it is zero unless the records show a second quantity that a person should confirm.
11. **Credits and amendments.** Link every amendment and credit to the invoice line or lines of its account. An amendment that changes a quantity or price in the period and is not reflected in the line is cited as evidence on that line's difference. A credit dated in the period that has no credit line on the draft is a difference of kind "credit not on the draft". The credit has no invoiced line of its own: it is attached to the account's invoice line, and that line goes in the "difference computed" group at its invoiced amount, even when its own quantity, price and arithmetic are right. Set the item out as the line's invoiced figures, the credit and its date, the expected net (the line amount plus the credit, the credit being negative) and the amount by which the draft is above it. If the line has another difference as well, give each its own E-number; the line still counts once. A credit has no line to attach to when the account has no invoice line; list it under credits and amendments as unlinked and in "Held open" without a line number, and leave it out of the line groups and their amounts. An amendment or credit with no account in the export is also listed as unlinked and held open.
12. **Add up.** Put every invoice line in exactly one group: clean, difference computed, or held open. A line with only a credit not on the draft is in "difference computed", never "clean". Only invoice lines are counted in the groups; a credit not on the draft is a figure inside the "difference computed" group, not an extra line. Check that the three groups, by invoiced amount, add up to the total of the invoice lines. If they do not, stop and report the figures.
13. **Questions and decisions.** For each item write one question for the billing specialist that names the record to look at. Write the decisions that belong to finance, as numbered questions: correct or leave, apply a credit, add to this run or the next, how the open items are billed. Recommend none unless the finance lead asks. For a dispute, add what the customer said and which items bear on it.
14. **Trace and return.** Name the inputs behind every figure. Return the sheet to the billing specialist only.

## Exceptions and stop conditions

- **A header does not match, or a required file is missing:** stop and say which.
- **The groups do not add up to the invoice total:** stop and report the figures and the difference.
- **Two mapping rows apply to the same plan and date:** stop; ask which is approved.
- **Currency differs between a line and the mapping:** hold the line open; compute nothing.
- **A line cannot be placed in a group:** hold it open and say why. Never force a match.
- **Asked to change an invoice, apply a credit, send anything to a customer, set a price, or decide whether a charge is right in law or in the accounts:** decline. The billing specialist verifies, and the finance lead approves.

## Output format

```
BILLING EXCEPTION SHEET: [run name, or "Disputed charge" with account and invoice]

For: [Billing specialist], to verify; [finance lead], to approve. Period [start] to [end]. Prepared from [the inputs supplied].

Inputs read: [n] subscription rows, [n] price-mapping rows, [n] seat or usage rows, [n] invoice lines totalling [total], [n] amendments or credits. Headers matched: [yes, or the mismatch].

Result: [n] lines clean ([amount]). [n] lines with a difference computed ([invoiced amount]), of which [n] with a credit not on the draft. [n] lines held open ([invoiced amount]). [n] subscriptions not billed. Check: [clean] + [computed] + [open] = [total].

Differences computed:
- [E-number, line, account, plan. Kind. Invoiced quantity, price and amount. Records or mapping. Expected amount. Difference, and which way.]
- [For a credit not on the draft: E-number, line, account, plan. Kind. Invoiced figures, which agree. The credit and its date. Expected net. Draft above expected by.]
(If none: "None.")

Held open, nothing computed:
- [E-number, line, account, plan. Kind. What the records show. What is missing.]
(If none: "None.")

Not billed:
- [E-number, account, plan, status, recorded quantity, expected amount.]
(If none: "None.")

Credits and amendments:
- [Account, date, type, amount: the line or item it links to, or "unlinked".]
(If none supplied: "Not supplied." If none apply: "None.")

Clean lines: [line numbers, with account and the checks passed. A line with a credit not on the draft is not here.]

Could not be assessed: [what was left unchecked and why, or "Nothing."].

Questions for the billing specialist:
1. [Item and the record to check.]

Decisions for finance: [n].
1. [Decision, with the facts.]

Every figure traces to [the inputs]. The sheet issues and changes no invoice and sends nothing.
```

## Reviewer checklist

1. Every header matched the defaults, and the row counts agree with the files. (Billing specialist)
2. The three groups add up to the invoice total. (Billing specialist)
3. Every computed difference uses the mapped price and the recorded quantity, and the arithmetic is right. (Billing specialist)
4. No ambiguous account has been matched by quantity, amount or similarity. (Billing specialist)
5. Every mid-period change and bundled line is held open with nothing computed unless a rule was supplied. (Billing specialist)
6. Every amendment and credit is linked to a line or listed as unlinked. (Billing specialist)
7. Every item has a question and no decision has been taken for finance. (Finance lead)
8. Nothing has been issued, changed or sent. (Finance lead)

## Acceptance tests

Proposed tests. None has been run.

1. **Clean run.** All lines agree with the mapping and the records. Expected: all lines clean, every other section "None.", the check adds up.
2. **Quantity after an amendment.** The line bills 10 seats at $45.00; records show 8 from the first of the month; an amendment says so. Expected: kind quantity, expected $360.00, difference $90.00 above, the amendment cited.
3. **Price off the mapping.** 25 seats at $28.00 against a $25.00 mapping. Expected: expected $625.00, difference $75.00 above.
4. **Ambiguous account.** A blank id and the name "Customer H", with two subscriptions named "Customer H Europe" and "Customer H North America". Expected: held open with both candidates listed, neither chosen, neither listed as not billed.
5. **Mid-period change, no rule.** Seats change on the fifteenth. Expected: held open, both quantities and dates shown, no expected amount.
6. **Bundle above its allowance.** 62 thousand calls against 50 included, mapping silent on excess. Expected: held open, the bundle price confirmed as a whole, nothing computed for the excess.
7. **Not billed.** An active subscription with 10 seats on record and no line. Expected: listed as not billed at 10 × the mapped price.
8. **Header mismatch.** The invoice file has `qty` where `quantity` is expected. Expected: stop, list the headers, ask.
9. **Credit not on the draft, figures right.** Line 40 x $25.00 = $1,000.00 agrees with the mapping and records; a -$100.00 credit has no line. Expected: the line is in the difference-computed group, not clean; expected net $900.00; the Result line says "of which 1 with a credit not on the draft".
10. **Bundle quantity.** A bundle line bills 1 while seat records show 10. Expected: no quantity difference; the line is held open or clean under the bundle step only.
11. **Asked to issue a credit.** Expected: declines and points to the finance lead.

## Instructions for the AI assistant

```
You prepare a billing exception sheet for a billing specialist at a
company that bills subscriptions. You issue and change no invoice, apply
no credit, send nothing to a customer and take no accounting or tax
position. The billing specialist verifies every exception; the finance
lead approves any correction, credit or revised invoice. You decide none
of it.

The user will supply these, with these headers:
- Settings: billing period, currency, tolerance (default 0.00), seat
  basis (default: quantity on record at the period start), the rule for a
  quantity that changes in the middle of a period (default: none), and
  the usage measure name for each usage plan and each usage amount in a
  bundle.
- Subscription export: account_id, account_name, plan_code, quantity,
  term_start, term_end, billing_cycle, status.
- Approved price mapping: plan_code, plan_name, billing_unit, unit_price,
  currency, billing_cycle, includes, effective_from.
- Seat and usage records: account_id, measure, period_start, period_end,
  quantity.
- Invoice lines: line, account_id, account_name, plan_code, quantity,
  unit_price, amount, period_start, period_end, with a reference for the
  run or invoice.
- Amendments and credits: account_id, date, type, detail, amount.
If a header does not match, stop, list the headers found against those
expected, and ask. If the period, currency, mapping, records or invoice
lines are missing, stop and say so. If amendments and credits are
missing, say so in that section and continue.

1. Count the rows in each file. Confirm each line's period lies inside
   the billing period; a line with another period is held open.
2. Check quantity x unit price = amount for each line, to the cent.
3. Match each line to an account by account_id. If it is blank or
   unknown, compare names ignoring case, spaces and punctuation: use a
   single identical name and say the name was the basis. Otherwise it is
   an ambiguous account: list as candidates every export name that
   contains the line's name or is contained in it, with plan and
   quantity, hold the line open, and never choose one on quantity,
   amount or similarity. Candidates are not also listed as not billed.
4. Check the plan is in the mapping and held by the account, active and
   in term. If not, kind "billed outside the term", expected zero.
5. Check the unit price against the mapping row in force on the period
   start, within the tolerance. Expected = invoiced quantity x mapped
   price.
6. Quantity: a bundle line skips this check and step 8 governs it. For a
   seat plan, check quantity against the seat records covering the period
   start. For a usage plan, use the measure name the settings give for
   that plan (stop and ask if none is given): one record whose span
   equals the period, or records whose spans together cover it exactly,
   summed. If no record covers it, hold open as "no record" with no
   amount. Expected = recorded quantity x mapped price.
7. If a second quantity starts inside the period, hold the line open as
   a mid-period change; show both quantities and dates. Compute an
   amount only if the settings give a rule, and label it as the rule's
   result.
8. For a bundle, check the price as a whole, then the records against
   what it includes. If a measure exceeds it or the mapping is silent
   on excess, hold open and compute nothing. Never split a bundle.
9. List active, in-term subscriptions with records and no line as not
   billed, with the expected amount, unless they are candidates of an
   ambiguous line. A usage plan with no record is listed as "no record",
   with no amount.
10. Two lines for the same account, plan and period are a duplicate; the
    second is queried and its expected amount is zero.
11. Link every amendment and credit to its line. An amendment not
    reflected in a line is cited on that line's difference. A credit with
    no credit line on the draft is "credit not on the draft". Its invoice
    line goes in "difference computed" at its invoiced amount, even if
    its own figures are right; set the item out as the invoiced figures,
    the credit and date, the expected net and the amount the draft is
    above it. A credit with no invoice line to attach to, and an
    amendment or credit whose account is not in the export, is listed as
    unlinked and held open, outside the line groups.
12. Put each invoice line in exactly one group: clean, difference
    computed or held open. A line with only a credit not on the draft is
    never clean. The groups must add up to the invoice total. If they do
    not, stop and report the figures.
13. Write one question per item for the billing specialist, naming the
    record to look at, and the decisions for finance as numbered
    questions. Recommend nothing unless asked.
14. Use the output format exactly, with every section present, and
    print "None." for an empty one. Name the inputs behind every figure
    and end with the trace line. Return the sheet to the billing specialist
    only.

Stop and ask if two mapping rows apply to the same plan and date. Hold a
line open, computing nothing, if its currency differs from the mapping.

Never adjust a figure to make it agree. If asked to issue, change,
credit, send or decide, decline.
```

## What to customize

- Your plan codes, price mapping and the export that is its single source.
- Your seat basis and your rule for mid-period changes, or leave the rule unset.
- The measure name each usage plan and each bundled usage amount is recorded under in your usage export.
- Your tolerance and the amount above which a correction needs a second approver.
- The column names in your exports, mapped to the defaults once.
- Who verifies, who approves, and who receives the sheet.
- Which exports the assistant may read in ChatGPT, Claude, Copilot or Gemini.

## Version notes

- 0.1.0, 10 November 2026. Written by Fully Powered AI. Not yet tested in a client environment.

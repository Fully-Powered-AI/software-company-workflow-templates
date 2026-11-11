---
name: "subscription-billing-exception-sheet"
description: "Prepare the sheet a billing specialist works from before a subscription billing run or when a customer disputes a charge. It ties each account's plan, quantity and invoice lines to the approved price mapping and to the seat or usage records, shows each difference with the amounts behind it, and keeps every doubtful item open: ambiguous account matches, mid-period changes and bundled lines. The assistant prepares and checks. It issues and changes no invoice, applies no credit and takes no accounting or tax position. The billing specialist verifies every exception, and the finance lead approves any correction, credit or revised invoice."
license: "MIT"
metadata:
  version: "0.1.0"
  publisher: "Fully Powered AI"
  capability: "Subscription billing exception sheet"
---

# Subscription billing exception sheet

This is the technical file for a Fully Powered capability template. It carries the instructions an AI product follows. The complete template, with roles, inputs, exceptions, the reviewer checklist, acceptance tests and what to customize, is in [TEMPLATE.md](TEMPLATE.md). A worked example with invented data is in [EXAMPLE.md](EXAMPLE.md).

## Instructions

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

## Before relying on it

Decide every item under "What to customize" in TEMPLATE.md and set the limits the instructions in this file leave open, written in square brackets such as [N], to your own. Then run the acceptance tests in TEMPLATE.md on past work. A person starts this work, supplies the inputs and decides what happens with the result.

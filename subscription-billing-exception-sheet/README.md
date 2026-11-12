# Subscription billing exception sheet

Before a subscription billing run, or when a customer disputes a charge, the billing specialist gets a sheet tying each account's plan, quantity and invoice lines to the approved price mapping and the seat or usage records, with doubtful matches kept open.

*Workflow template · Software technology · Finance and accounting · version 0.1.0 · [Workflows Directory](https://fullypowered.ai/workflow templates/subscription-billing-exception-sheet/)*

## The outcome

Most subscription charges are right. The few that are not are the ones a customer finds first: a seat count that fell on the first of the month, a price that moved off the list, an account that was never invoiced, a credit that was agreed but never reached the invoice. This workflow template finds them before the run goes out, or traces a disputed charge back to the records behind it.

The billing specialist spends the review on the exceptions rather than on lines that agree. Where a match is doubtful, because the account name fits two accounts, the plan changed in the middle of the period, or one line bundles several things, the sheet says so and leaves the item open. It never picks the likely answer. The sheet issues and changes no invoice and takes no accounting or tax position.

## Who starts the work, and when

The billing specialist or the revenue operations lead starts it when the draft invoice lines for a run are ready, or when a customer questions a charge and the account needs tracing. The billing specialist verifies each exception against the records. The finance lead approves any correction, credit or revised invoice.

## What they supply

- The subscription export: one row per account and plan, with quantity, term dates and status.
- The approved price mapping: each plan's unit price, billing unit and, for bundles, what is included.
- The seat or usage records for the period, with the dates each quantity applied.
- The draft or issued invoice lines for the run, or for the disputed invoice.
- Amendments and credits recorded since the last run.
- Your settings: the billing period, the tolerance, and your rule for mid-period changes if you have one.

## What comes out

A billing exception sheet, in a fixed order. It gives a check that the lines add up to the invoice total, each difference with the amounts behind it, the items held open and why, the subscriptions that were not billed, the credits and amendments linked to their lines, and the questions for the billing specialist and the decisions for finance.

See the worked example with invented data in [EXAMPLE.md](EXAMPLE.md).

## Where it fits

- [Software and technology companies](https://fullypowered.ai/industries/software-technology/), where plans, seats and usage change between billing runs.
- [Media and entertainment](https://fullypowered.ai/industries/media-and-entertainment/), where memberships and licences are billed on a recurring basis.
- [Ecommerce and retail](https://fullypowered.ai/industries/ecommerce-and-retail/), where subscription programmes are billed from plan and quantity records.
- [Finance and accounting](https://fullypowered.ai/functions/finance-and-accounting/), which owns the invoice, the credit and the close.
- [Growth & scaling](https://fullypowered.ai/situations/growth-and-scaling/), when plan counts and amendments outgrow a spreadsheet check.
- [Established businesses](https://fullypowered.ai/situations/established-businesses/), where an older price list and years of amendments hide exceptions.

It looks at what the company charges its own customers. It stays apart from [receivables exception review](https://fullypowered.ai/workflows/receivables-exception-review/), which handles payments that came in against issued invoices, from [payout reconciliation for an online store](https://fullypowered.ai/workflows/payout-reconciliation-for-an-online-store/), which ties a payment processor's payouts to the bank, and from [supplier bill review and payment run preparation](https://fullypowered.ai/workflows/supplier-bill-review-and-payment-run-preparation/), which checks bills the company owes.

## What has to change for your company

Supply your own plan codes and price mapping, and say which export is the single source of the mapping. Set your rule for seats that change in the middle of a period, or leave it unset so every such change stays open. Decide who verifies exceptions and who approves credits, and above what amount. Set the tolerance, which starts at none. Map your export's column names to the defaults, or rename them once.

## What has been checked

Fully Powered AI wrote this workflow template. It was editorially reviewed on 10 November 2026. It was tried once on its invented example in Claude on 10 November 2026, and the record is published with it. Any edits made after the trial have not been run again. It has not yet been tested in a client environment. It has not yet been tested as a packaged version in ChatGPT, Claude, Copilot or Gemini.

Testing in your environment means running it on a past billing run the specialist already knows, with cases written in advance: a changed seat count, an account with two similar names, a bundle, a credit not on the invoice. The billing specialist checks every figure against the records before anyone relies on the sheet.

- Written by Fully Powered AI.
- Sources and rights reviewed.
- Editorially reviewed on 10 November 2026.
- Package format checked by script on every release.
- Tried once on its invented example in Claude on 10 November 2026. The record is in [TRIAL.md](TRIAL.md).
- Not yet tested in a client environment.

## What is in this folder

- [TEMPLATE.md](TEMPLATE.md): the complete workflow template. Roles, inputs, the procedure, exceptions and stop conditions, the output format, a reviewer checklist, acceptance tests, the instructions for an AI assistant and what to customize.
- [EXAMPLE.md](EXAMPLE.md): a worked example with invented data.
- [TRIAL.md](TRIAL.md): what came out when the template was tried on its example.
- [SKILL.md](SKILL.md): the technical file, for AI products that load packaged instructions from a folder.
- [SOURCES.md](SOURCES.md): what the workflow template drew on, with licences.
- [LICENSE](LICENSE): MIT. Use it, change it, make it yours.

## Start using it

1. Read [EXAMPLE.md](EXAMPLE.md) to see what a good result looks like.
2. Open [TEMPLATE.md](TEMPLATE.md) and set every item under "What to customize" to your own rules, roles and limits.
3. Give your AI assistant the instruction block and the output format from the template, with your own limits in place of the ones the instructions leave open in square brackets. Paste them in as custom instructions in ChatGPT, Claude, Copilot or Gemini, or copy this whole folder into a product that loads `SKILL.md` packages. This folder stands alone; you do not need the rest of the repository.
4. Run it on past work first, using the reviewer checklist and acceptance tests in the template, before anyone relies on it.

## Related workflow templates

- [Receivables exception review](https://fullypowered.ai/workflow templates/receivables-exception-review/)
- [Month-end close checklist](https://fullypowered.ai/workflow templates/month-end-close-checklist/)
- [Software subscription and vendor spend review](https://fullypowered.ai/workflow templates/software-subscription-and-vendor-spend-review/)

## Make it yours

This is the starting version. Fully Powered AI adapts workflow templates to how your company works, proves them on real work and rolls them out to the roles that use them. [Talk with us](https://fullypowered.ai/contact/).

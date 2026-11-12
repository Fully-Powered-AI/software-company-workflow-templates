# Buyer security questionnaire answers

When a buyer sends a security questionnaire, your sales owner gets a draft answer matrix: each question beside the evidence your security owner supplied, its date, its limits and a named reviewer, with stale, partial and unverifiable answers marked.

*Workflow template · Software technology · Sales · version 0.1.0 · [Workflows Directory](https://fullypowered.ai/workflows/buyer-security-questionnaire-answers/)*

## The outcome

The questionnaire stops being a scramble across sales, security and IT. The sales owner has one matrix in which every question is either answered from evidence the security owner has already supplied, or marked with the reason it cannot yet be: the evidence is out of date, covers only part of the question, or does not exist.

A written policy is never treated as proof that the practice is in place. Where only a policy exists, the matrix says so. The draft answers use the security owner's approved wording and nothing else, so the people who verify them are checking sources, not rewriting prose.

## Who starts the work, and when

The sales owner starts it the day a buyer's questionnaire arrives, or when a buyer asks follow-up questions on an earlier one. The security owner supplies the evidence and verifies every answer. Named reviewers, such as the IT lead for hosting and backups, confirm the answers in their area. Sales sends only the response the security owner has approved for disclosure.

## What they supply

- The buyer's questions, as a file or a list with a reference number for each.
- An evidence register from the security owner: approved policies, configuration exports and test records, each with its scope, source date, limits and owner.
- The rules for this response: how old evidence may be, what may be shared with this buyer and on what terms, and who reviews each topic.
- Any earlier correspondence with this buyer that changes what was asked.

## What comes out

One draft answer matrix. Each question carries a mark (supported, partial, stale or unverifiable), a draft answer in the security owner's own approved wording, the evidence behind it with its date and age, its limits, and a named reviewer. The matrix ends with the counts, the answers that need a disclosure decision, and the questions held for the security owner, each as a question for a named person.

It is a draft. It assesses no security control and claims no compliance, and it sends nothing.

See the worked example with invented data in [EXAMPLE.md](EXAMPLE.md).

## Where it fits

- [Sales](https://fullypowered.ai/functions/sales/), where a stalled questionnaire holds up a deal that is otherwise ready.
- [Information security](https://fullypowered.ai/functions/information-security/), which owns the evidence and decides what a buyer may be told.
- [Software and technology](https://fullypowered.ai/industries/software-technology/), where buyers send security questionnaires routinely before they sign.
- [Finance and investment](https://fullypowered.ai/industries/finance-and-investment/), where a software supplier's controls are examined before any data is shared.
- [Healthcare](https://fullypowered.ai/industries/healthcare/), where buyers ask detailed questions of a software supplier that will touch their records.
- [Growth & scaling](https://fullypowered.ai/situations/growth-and-scaling/), when questionnaires arrive faster than one security owner can answer them.
- [Established businesses](https://fullypowered.ai/situations/established-businesses/), when the evidence exists but is scattered across teams.

It is separate from [bid-or-no-bid and RFP response plan](https://fullypowered.ai/workflows/bid-or-no-bid-and-rfp-response-plan/), which decides whether to respond to a request and plans the whole response, and from [sales proposal preparation](https://fullypowered.ai/workflows/sales-proposal-preparation/), which drafts the proposal. This workflow template handles one part of either: the security questions.

## What has to change for your company

Set how old each kind of evidence may be before it counts as stale. Decide who reviews which topic, and who may approve disclosure. Agree what may be shared with a buyer, for example summaries freely and reports only under a confidentiality agreement. Fix the column headings of your evidence register once and keep to them. Keep the register in one place the security owner maintains, since the matrix can only be as current as that register.

## What has been checked

Fully Powered AI wrote this workflow template. It was editorially reviewed on 10 November 2026. It was tried once on its invented example in Claude on 10 November 2026; the record of that run is published with it. It has not yet been tested in a client environment. It has not yet been tried as a packaged version in ChatGPT, Claude, Copilot or Gemini.

Testing in your environment means running it on a questionnaire you have already answered, with cases written in advance: a policy with no configuration evidence, an export past its age limit, a question with no evidence at all, two sources that disagree. The security owner checks every answer against its source before anyone relies on it. [Pilot acceptance-test preparation](https://fullypowered.ai/workflows/pilot-acceptance-test-preparation/) sets those cases up.

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

- [Bid or no-bid and RFP response plan](https://fullypowered.ai/workflows/bid-or-no-bid-and-rfp-response-plan/)
- [Sales proposal preparation](https://fullypowered.ai/workflows/sales-proposal-preparation/)
- [Deal close plan](https://fullypowered.ai/workflows/deal-close-plan/)

## Make it yours

This is the starting version. Fully Powered AI adapts workflow templates to how your company works, proves them on real work and rolls them out to the roles that use them. [Talk with us](https://fullypowered.ai/contact/).

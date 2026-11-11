# Fully Powered Capability Templates: Software Companies

The business side of a software company, running as smoothly as the product. These capability templates are written for the people around the code: support, success, sales, product and finance. They prepare the briefs, plans and checks from your own records. They are not developer tooling, and they certify nothing about your security.

This repository holds 6 capability templates for the support, success, sales, product and finance people at a software company. Each one is a single piece of work with its own folder: what it is for and who starts it, the complete template an AI assistant follows, a worked example with invented data, what to change for your company, what has been checked, and its sources.

## The capabilities

- **[Buyer security questionnaire answers](buyer-security-questionnaire-answers/)**: When a buyer sends a security questionnaire, your sales owner gets a draft answer matrix: each question beside the evidence your security owner supplied, its date, its limits and a named reviewer, with stale, partial and unverifiable answers marked.
- **[Cloud spend variance bridge](cloud-spend-variance-bridge/)**: When cloud or tooling costs move away from budget, the finance lead and the engineering manager get a bridge from budget to actual by service and cost owner, with usage beside each large move, the unallocated and shared costs, and the questions each side must answer.
- **[Implementation blocker brief](implementation-blocker-brief/)**: When a customer's setup milestone slips, the implementation lead gets one brief: the missing inputs, the unresolved access and data questions and the dependencies behind the delay, each with its source and an owner, plus points to raise with the customer.
- **[Subscription billing exception sheet](subscription-billing-exception-sheet/)**: Before a subscription billing run, or when a customer disputes a charge, the billing specialist gets a sheet tying each account's plan, quantity and invoice lines to the approved price mapping and the seat or usage records, with doubtful matches kept open.
- **[Technical demo plan](technical-demo-plan/)**: Before a technical discovery or demo meeting, the account executive and solutions engineer get an attendee brief, a demo sequence built around the buyer's stated workflow from approved scenarios, and open questions. Requests nobody has verified stay questions.
- **[Usability test session plan](usability-test-session-plan/)**: Before a prototype or a confusing flow goes in front of users, the research lead and product owner hold one plan: who to recruit, the tasks in plain words, the neutral prompts, a blank note sheet and how success is counted. Recording and data handling are listed as decisions.

## How to use one

Open a folder and start with its README. Every folder stands alone, so copy the one you want and leave the rest. The templates are written for ChatGPT, Claude, Copilot and Gemini: paste the instruction block and the output format in as custom instructions, or load the folder in a product that reads `SKILL.md` packages.

In every template a person starts the work, supplies the inputs and decides. The template prepares and checks. Anything that sends, posts, pays or changes a record waits for a person to approve it.

## What SKILL.md is

Each folder holds a file named `SKILL.md`. It is the technical file: the same instructions and output format as the template, in the packaged form that AI products which load instructions from a folder read. It is generated from `TEMPLATE.md`, so the two always agree. The capability template is the whole folder; `SKILL.md` is one way of loading it. If your AI product does not read that format, use `TEMPLATE.md`.

## What "checked" means here

Each folder says exactly what was checked and when: who wrote it, that its sources and rights were reviewed, the date of its editorial review, and whether it has been tried on its invented example in a named AI product. Nothing is described as tested for a client unless it was. Test a template on your own past work before your team relies on it; each one comes with acceptance tests for that.

## More capabilities

The [Fully Powered Capabilities Directory](https://fullypowered.ai/capabilities/) lists every capability across functions and industries, with search. A machine-readable list of this repository is in [index.json](index.json).

## Licence and credits

MIT, in [LICENSE](LICENSE) and in every folder. Each folder's SOURCES.md names what the capability drew on. Published by [Fully Powered AI](https://fullypowered.ai/).

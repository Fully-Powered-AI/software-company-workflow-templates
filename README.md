# AI workflow templates for software company teams

FullyPowered Workflow Templates for software companies turn the AI your company already pays for into a team that knows how the work is done: a sales team with the buyer security questionnaire answered and sourced, a finance lead with the cloud spend variance bridged, a research lead with the usability test session planned. 6 workflow templates, made to be customized and deployed. All plain Markdown, all free, MIT license.

We are FullyPowered AI. We build AI workflows for companies, and these are the templates we start from. We publish them because a good starting point should be open to everyone. Copy one. Change it. Make it yours.

> [!TIP]
> **Missing a template that is not listed here, or want these customized for your organization? Reach out to us.** These are templates, made to be customized and deployed. FullyPowered AI customizes and builds AI workflows, connects them to your business systems, installs them in your agents and puts them in the hands of the people who own the work. [See more examples for software companies](https://fullypowered.ai/industries/software-technology/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=software-company-readme&from=gh-software-company-readme) · [Have one built for your team](https://fullypowered.ai/pricing/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=software-company-readme&from=gh-software-company-readme). Not sure where to start? Email hello@fullypowered.ai and a person will answer.

**Who this is for**

- Founders and executives at software companies who have paid for AI and want it doing real work.
- Heads of sales, support, success, product and finance who want something their team can run this week.
- The account executive, billing specialist or researcher who gets a precise way to prepare and still decides.

**What these are for**

- **Your best way of doing it, for the whole team.** One piece of work, written down precisely enough that an assistant prepares it the same way every time.
- **Work you can check.** Every template says what it needs, what it produces, what it checked and what it could not.
- **A person decides.** Anything that sends, posts, pays or changes a record waits for someone to approve it.
- **Tied into your business systems.** A workflow can be designed to pull from the systems your company already runs, and even push data back into them, with guardrails and a person approving. [Browse the Connectors Directory](https://fullypowered.ai/connectors/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=software-company-readme&from=gh-software-company-readme).
- **Free, open and portable.** MIT-licensed plain instructions that run in the assistant or agent your team already uses: ChatGPT, Claude, Claude Code, Claude Cowork, Codex, Copilot, Gemini, Grok, Perplexity.

**Quick start**

1. **Turn a buyer's security questionnaire into a draft answer sheet.** Open ChatGPT, Claude, Copilot or Gemini. Paste the text below, then add the buyer's questions and your security owner's list of approved statements. Nothing needs to be installed or signed up for.

   ```text
   You are helping a sales owner prepare a draft answer sheet for a buyer's
   security questionnaire. A person decides everything. You send nothing,
   change nothing and assess no security control. I will paste: (1) the
   buyer's questions with a reference number each, (2) a list of evidence
   from our security owner, with each item's approved statement, type,
   scope, date and limits, and (3) today's date and how old each kind of
   evidence may be. Use only that list. For each question give: a mark
   (Supported, Partial, Stale or Unverifiable), a draft answer using the
   approved wording only, the evidence and its date, its limits, and who
   should review it. A policy alone is never proof that the practice is in
   place. If two items disagree, show both and choose neither. End with
   counts and the questions held for named people. [Paste your questions,
   evidence list and date here.]
   ```

2. Read what comes back. It marks what it checked and what is left for you. What comes out, with invented data:

   ```text
   BUYER SECURITY QUESTIONNAIRE ANSWERS: Buyer X, 8 questions

   For: Alicia Ward (sales owner). Verified by: Dana Kessler (security owner). Questionnaire received 2 November 2026. As of 10 November 2026.

   Freshness limits used: policies, test records and certificates not older than 10 November 2025; configuration exports not older than 12 August 2026.

   Q1: Is customer data encrypted at rest?
     Mark: Partial
     Draft answer: Production database and file storage volumes are encrypted at rest with AES-256.
     Evidence: E1, configuration export, 2026-10-06, 35 days old, in date.
     Limits: backups are not covered by this export. The question asks about customer data, and backups hold customer data.
     Reviewer: Tomas Rehn.
   ```

3. Stop there. You will know if this is for you. When you want it fitted to your company, or built into your agents, [that is what we do](https://fullypowered.ai/pricing/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=software-company-readme&from=gh-software-company-readme).

In every one of these workflow templates, a person starts the work, supplies the inputs and makes the decisions, while the template prepares and checks.

These are examples and a starting point, made to be changed for your own company, your own records and your own rules. Work that is not listed here can still be built for your team, as one step or as many.

## The workflow templates here today

- **[Buyer security questionnaire answers](buyer-security-questionnaire-answers/)**: When a buyer sends a security questionnaire, your sales owner gets a draft answer matrix: each question beside the evidence your security owner supplied, its date, its limits and a named reviewer, with stale, partial and unverifiable answers marked.
- **[Cloud spend variance bridge](cloud-spend-variance-bridge/)**: When cloud or tooling costs move away from budget, the finance lead and the engineering manager get a bridge from budget to actual by service and cost owner, with usage beside each large move, the unallocated and shared costs, and the questions each side must answer.
- **[Implementation blocker brief](implementation-blocker-brief/)**: When a customer's setup milestone slips, the implementation lead gets one brief: the missing inputs, the unresolved access and data questions and the dependencies behind the delay, each with its source and an owner, plus points to raise with the customer.
- **[Subscription billing exception sheet](subscription-billing-exception-sheet/)**: Before a subscription billing run, or when a customer disputes a charge, the billing specialist gets a sheet tying each account's plan, quantity and invoice lines to the approved price mapping and the seat or usage records, with doubtful matches kept open.
- **[Technical demo plan](technical-demo-plan/)**: Before a technical discovery or demo meeting, the account executive and solutions engineer get an attendee brief, a demo sequence built around the buyer's stated workflow from approved scenarios, and open questions. Requests nobody has verified stay questions.
- **[Usability test session plan](usability-test-session-plan/)**: Before a prototype or a confusing flow goes in front of users, the research lead and product owner hold one plan: who to recruit, the tasks in plain words, the neutral prompts, a blank note sheet and how success is counted. Recording and data handling are listed as decisions.

## How to use one

Open a folder and start with its README. Every folder stands alone, so copy the one you want and leave the rest. The templates are written for ChatGPT, Claude, Copilot and Gemini: paste the instruction block and the output format in as custom instructions, or load the folder in a product that reads `SKILL.md` packages.

To take the whole collection, press **Use this template** at the top of this page: it copies every folder into a repository in your own account, yours to change.

In every template a person starts the work, supplies the inputs and decides. The template prepares and checks. Anything that sends, posts, pays or changes a record waits for a person to approve it.

## What SKILL.md is

Each folder holds a file named `SKILL.md`. It is the technical file: the same instructions and output format as the template, in the packaged form that AI products which load instructions from a folder read. It is generated from `TEMPLATE.md`, so the two always agree. The workflow template is the whole folder; `SKILL.md` is one way of loading it. If your AI product does not read that format, use `TEMPLATE.md`.

## What "checked" means here

Each folder says exactly what was checked and when: who wrote it, that its sources and rights were reviewed, the date of its editorial review, and whether it has been tried on its invented example in a named AI product. Nothing is described as tested for a client unless it was. Test a template on your own past work before your team relies on it; each one comes with acceptance tests for that.

## More workflow templates

The [FullyPowered Workflows Directory](https://fullypowered.ai/workflows/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=software-company-readme&from=gh-software-company-readme) lists every workflow template across functions and industries, with search. A machine-readable list of this repository is in [index.json](index.json).

For the work these templates come from, by area of the business and by task, see [AI workflow examples for software companies](https://fullypowered.ai/industries/software-technology/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=software-company-readme&from=gh-software-company-readme).

## Licence and credits

MIT, in [LICENSE](LICENSE) and in every folder. Each folder's SOURCES.md names what the workflow template drew on. Published by [FullyPowered AI](https://fullypowered.ai/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=software-company-readme&from=gh-software-company-readme).

# Implementation blocker brief

When a customer's setup milestone slips, the implementation lead gets one brief: the missing inputs, the unresolved access and data questions and the dependencies behind the delay, each with its source and an owner, plus points to raise with the customer.

*Capability template · Software technology · Customer success and account management · version 0.1.0 · [Capabilities Directory](https://fullypowered.ai/capabilities/implementation-blocker-brief/)*

## The outcome

The implementation lead walks into the next customer call knowing exactly what is holding the work up, not just that it is late. Every late milestone is traced to the things stopping it: something the customer has not supplied, an access question nobody has settled, a data question, a change window, or an earlier milestone that is itself unfinished.

Each blocker carries where it was recorded, how long ago, who owns it on the customer's side and on yours, and whose move it is. Where the records say nothing, the brief says so instead of filling the space.

## Who starts the work, and when

The implementation lead starts it when a milestone passes its planned date, or when the customer's project owner says one will. The solutions engineer corrects anything about integrations and data. The customer success manager adds what the customer has said outside the project calls. The AI assistant prepares the brief. It never contacts the customer, never confirms that access works and never proposes, computes or promises a new date. The lead agrees the recovery plan and any revised dates with the customer.

## What they supply

- **The implementation plan,** with each milestone's planned date, status, owners and what it depends on.
- **The readiness checklist,** the list of inputs, access and data the customer owes, with status and owners.
- **Integration notes,** as your engineers wrote them.
- **Recent customer meeting records,** with dates.
- **Today's date,** which the person states.

## What comes out

1.  **A summary.** How many milestones are late, how many blockers, whose move each waits on.
2.  **The late milestones,** with days late and what holds each up, and the later milestones that wait on them.
3.  **The blockers,** one block each: type, what it holds up, status, owners on both sides, latest record and sources.
4.  **Where the records disagree, and gaps.**
5.  **The dates the records state.**
6.  **Points for the customer conversation,** written as questions, with your own side's tasks first.

Good looks like this: the lead could open the customer call with the brief alone, and every line points back to a record.

See the worked example with invented data in [EXAMPLE.md](EXAMPLE.md).

## Where it fits

- [Software technology](https://fullypowered.ai/industries/software-technology/): setup milestones depend on customer access, data and change windows.
- [Professional services](https://fullypowered.ai/industries/professional-services/): client-side inputs hold up delivery in the same way.
- [Customer success and account management](https://fullypowered.ai/functions/customer-success-and-account-management/): the first weeks decide whether the customer reaches value.
- [Project and delivery](https://fullypowered.ai/functions/project-and-delivery/): a late milestone needs its causes found before anyone re-plans.
- [Growth & scaling](https://fullypowered.ai/situations/growth-and-scaling/): more customers in setup than one lead can track by memory.
- [Startups & new ventures](https://fullypowered.ai/situations/startups-and-new-ventures/): a small team cannot afford a stalled first customer.

It stops at finding what is blocked. [Schedule recovery options](https://fullypowered.ai/capabilities/schedule-recovery-options/) lays out the ways back, [Customer onboarding plan](https://fullypowered.ai/capabilities/customer-onboarding-plan/) plans the weeks before a delay, and [Project handover readiness check](https://fullypowered.ai/capabilities/project-handover-readiness-check/) looks at the end of the work.

## What has to change for your company

- **Your export columns.** The default headers for the plan and the checklist, and your own status words.
- **What counts as a slip.** The default is any unfinished milestone past its planned date.
- **How blockers rank.** The default puts first the blocker holding up the most late milestones.
- **Who owns what.** Roles on both sides, and where the customer's owner is usually left blank.
- **Your platform.** It runs in ChatGPT, Claude, Copilot or Gemini. Decide which project records the assistant may read.

## What has been checked

Fully Powered AI wrote this capability template. It was editorially reviewed on 10 November 2026. It was tried once on its invented example in Claude on 10 November 2026; the record is published with it. The run on the revised template was made by the same session that revised it, so it was not independent, and it did not exercise the stop conditions or the acceptance tests. It has not yet been tested in a client environment. It has not yet been tested as a packaged version in ChatGPT, Claude, Copilot or Gemini.

Testing in your environment means running it on recent late implementations, with the expected behavior agreed first: access shown as confirmed only when a record says it works, an owner left blank in the checklist, a promise to send something "next week" with nothing since. [Pilot acceptance-test preparation](https://fullypowered.ai/capabilities/pilot-acceptance-test-preparation/) builds that test set.

- Written by Fully Powered AI.
- Sources and rights reviewed.
- Editorially reviewed on 10 November 2026.
- Package format checked by script on every release.
- Tried once on its invented example in Claude on 10 November 2026. The record is in [TRIAL.md](TRIAL.md).
- Not yet tested in a client environment.

## What is in this folder

- [TEMPLATE.md](TEMPLATE.md): the complete capability template. Roles, inputs, the procedure, exceptions and stop conditions, the output format, a reviewer checklist, acceptance tests, the instructions for an AI assistant and what to customize.
- [EXAMPLE.md](EXAMPLE.md): a worked example with invented data.
- [TRIAL.md](TRIAL.md): what came out when the template was tried on its example.
- [SKILL.md](SKILL.md): the technical file, for AI products that load packaged instructions from a folder.
- [SOURCES.md](SOURCES.md): what the capability drew on, with licences.
- [LICENSE](LICENSE): MIT. Use it, change it, make it yours.

## Start using it

1. Read [EXAMPLE.md](EXAMPLE.md) to see what a good result looks like.
2. Open [TEMPLATE.md](TEMPLATE.md) and set every item under "What to customize" to your own rules, roles and limits.
3. Give your AI assistant the instruction block and the output format from the template, with your own limits in place of the ones the instructions leave open in square brackets. Paste them in as custom instructions in ChatGPT, Claude, Copilot or Gemini, or copy this whole folder into a product that loads `SKILL.md` packages. This folder stands alone; you do not need the rest of the repository.
4. Run it on past work first, using the reviewer checklist and acceptance tests in the template, before anyone relies on it.

## Related capabilities

- [Schedule recovery options](https://fullypowered.ai/capabilities/schedule-recovery-options/)
- [Customer onboarding plan](https://fullypowered.ai/capabilities/customer-onboarding-plan/)
- [Project handover readiness check](https://fullypowered.ai/capabilities/project-handover-readiness-check/)

## Make it yours

This is the starting version. Fully Powered AI adapts capabilities to how your company works, proves them on real work and rolls them out to the roles that use them. [Talk with us](https://fullypowered.ai/contact/).

# Implementation blocker brief

Capability template, version 0.1.0.

## Purpose

When a customer's setup milestone slips, prepare one brief for the implementation lead: what is holding each late milestone up. Every blocker is a missing input, an unresolved access question, an unresolved data question, a customer change window or a dependency, and carries its source, how old the latest record is, whose move it waits on and an owner on the customer's side and on ours. The brief ends with points to raise with the customer, written as questions. The assistant prepares; it never contacts the customer, never confirms that integration access works and never proposes, computes or promises a new date. The lead agrees the recovery plan and any revised dates with the customer.

## When to use it and when not to

Use it when at least one milestone has passed its planned date without being done, or when the customer's project owner says one will. Run it again before each customer call while the milestone stays late.

Do not use it when:

- the question is how to get back on schedule, which routes to take or what the new dates should be. That is Schedule recovery options;
- the question is how to plan a new customer's first weeks. That is Customer onboarding plan;
- the work is finished and being handed to the team that runs it. That is Project handover readiness check;
- no milestone is late and nobody expects one to be. Nothing has slipped.

## Roles

- **Runs it and decides what happens next:** the implementation lead.
- **Corrects what the brief says about integrations, access and data:** the solutions engineer.
- **Adds what the customer has said outside the project calls:** the customer success manager.
- **Owns each blocker on the customer's side:** the person named in the plan or checklist.
- **Owns each blocker on our side:** the person named in the plan or checklist.
- **Agrees the recovery plan and any revised dates with the customer:** the implementation lead.

## Inputs

1. **Settings,** typed by the person: customer and project name, today's date, and what counts as a slip. The default is any milestone that is not done and whose planned date is before today. Today's date comes from the person, never from the assistant's own clock. If today's date is missing, ask for it.
2. **Implementation plan,** an export with these default headers: `milestone_id,milestone,planned_date,status,customer_owner,our_owner,depends_on`. Dates are YYYY-MM-DD. Status is one of `done`, `in progress`, `not started` or `blocked`. `depends_on` holds milestone ids separated by semicolons, or is blank. If a header or a status word does not match, stop and ask the person to map it. If the plan is missing, stop.
3. **Readiness checklist,** an export with these default headers: `item_id,item,category,needed_for,status,customer_owner,our_owner,last_update`. Category is one of `access`, `data`, `people`, `environment` or `other`. Status is one of `received`, `partial`, `not received` or `unknown`. `needed_for` holds milestone ids separated by semicolons. A blank owner means not assigned; a blank `last_update` means no date. If a header or a word does not match, stop and ask. If the checklist is missing, continue with blockers from the notes only and say so under gaps.
4. **Integration notes,** dated lines written by the engineers. If missing, say so under gaps and continue.
5. **Recent customer meeting records,** dated, with who was present. If missing, say so under gaps and continue.

If any input contains a password, key or login code, do not repeat it; tell the person to remove it from the file.

## The procedure

1. **Check the inputs.** Compare every header and status word with the defaults above. If one does not match, stop and ask. Note the date range of the notes and meeting records.
2. **Find the slipped milestones.** A milestone is slipped when its status is not `done` and its planned date is before today. Days late is today minus the planned date, in calendar days. If none is slipped, stop and tell the person; if they name a milestone the customer reports as slipping, treat it as slipped and write "days late: not applicable".
3. **Find the downstream milestones.** Every not-done, not-slipped milestone that waits, directly or through others, on a slipped one. For each, give the days from today to its planned date.
4. **List the checklist blockers.** Every checklist row whose status is not `received` and which is needed for a milestone that is not done. A row with a blank `needed_for` goes under gaps, not under blockers.
5. **List the blockers found only in the notes.** Anything in the integration notes or meeting records that stops, or may stop, a milestone and has no checklist row. Number these N1, N2 in the order of their dates. Include change windows and access that is mentioned but not requested. A named third party (for example a customer's security team) is not a blocker of its own: show it in the status or latest record of the blocker that waits on it, unless the record names something separate that the party must supply and no checklist row covers. Infer nothing the words do not say.
6. **Give each blocker a type.** From the checklist category: `access` is an access question, `data` is a data question, and `people`, `environment` and `other` are a missing input. From the notes: a change window, or a dependency when the record says it waits on a named party or on another blocker. A blocker is numbered B1, B2 in the order set in step 10.
7. **State what each holds up.** The milestones it is needed for, directly, then every milestone that depends on those, through the plan. For a notes-only blocker, link it to a milestone only when the record uses the milestone's id, its name, or a distinctive part of its name as the plan writes it (for example "single sign-on" for "Single sign-on connected"); show in the Holds up line the words that made the link. If no record does, write "link to a milestone not stated" and rank it by step 10 as holding up none.
8. **Attach the record.** For each blocker, the latest dated line in the notes or meeting records that concerns it, quoted where the exact words matter, and the number of days from that date to today. If only the checklist speaks, use its `last_update`; if it has none, write "no dated record". List every source: file, row or date. If one record line plainly concerns two blockers by its own words, quote it under both and say so; a line that does not name or describe a blocker's subject is not its record, and a doubt about that goes under gaps.
9. **Say whose move it is.** "Waiting on" is `customer`, `our side` or `not stated`, taken only from the words of the latest record. Do not decide it from the owner columns. Read a customer's own statement of a constraint, hold-back or pending action (that it can change settings only in a window, that it is holding something back until something else is agreed, that it is reviewing, or that it will name or send something) as `customer`. Read a record saying our side has not asked, sent or done something as `our side`. Use `not stated` only when the record does not say whose move it is, or no record speaks. Write exactly one of the three words, with nothing added.
10. **Rank the blockers.** First by the number of slipped milestones held up, most first; then by days since the latest record, longest first, with "no dated record" counted as the longest; then by item id, checklist rows before notes-only items.
11. **Owners.** The customer-side owner and our-side owner come from the plan and checklist columns or from the notes. A blank is "not assigned". Never choose an owner.
12. **Access.** Show access as confirmed only when a dated record says it works, from the customer or from a test our side reports. Otherwise show the status as recorded. If a later note contradicts a checklist status, keep the checklist status and list the contradiction under gaps.
13. **Gaps and disagreements.** Where sources disagree; where a blocker has no record since the checklist; where a slipped milestone has no blocker at all (write "no blocker recorded for [id]"); where a date in one source falls after a date in another that depends on it; where a customer statement gives no date (quote each one, with its source and which blocker it concerns).
14. **Dates in the record.** Every date the integration notes and meeting records state, other than the date of the record itself (for example a date a document was sent, or a customer's change window), with its source. The plan's planned dates, the checklist's `last_update` dates and the dates of the records are not listed here. A statement with no date ("next week", "before quarter-end", "no date") is listed under gaps, not here. Add none. Do not compute a new date.
15. **Points for the conversation.** First, "Our side first": a line for every blocker that waits on our side. Then exactly one numbered point per blocker waiting on the customer or not stated, never combined and never about anything that is not a blocker (a customer's stated need is a gap, not a point). Each is a question to a named customer role about that blocker, and ends "Concerns [the blocker id]". A point asks the customer to say what they can about the blocker as the record describes it; it does not ask about ways round it, which belong to schedule recovery options, offers no date and makes no commitment. The "Our side first" line states the blocker and the owner on our side, and gives no instruction.
16. **Return the brief** to the implementation lead only.

## Exceptions and stop conditions

- **A header or status word does not match the defaults:** stop and ask the person to map it.
- **The plan is missing:** stop.
- **No milestone is slipped:** stop, unless the person names one.
- **Today's date is missing:** ask for it.
- **A slipped milestone has no blocker in any source:** say so under gaps; do not invent a cause.
- **A record names a cause but no owner:** list the blocker with "not assigned" for the missing side.
- **An input contains a password, key or login code:** do not repeat it; tell the person to remove it.
- **Asked to contact the customer, send the points, confirm access works, state or propose a date, or choose between recovery routes:** decline. The implementation lead talks to the customer, and recovery routes belong to schedule recovery options.

## Output format

```
IMPLEMENTATION BLOCKER BRIEF: [Customer] / [Project]
Prepared [today's date] from: [each source, with its date or date range]. Days counted to [today's date].

SUMMARY
Late: [n] milestones ([id] [n] days, ...). Blockers: [n] ([n] waiting on the customer, [n] on our side, [n] not stated). Blockers missing an owner on either side: [n] ([B ids], or "none").

SLIPPED MILESTONES
[id] [milestone]: planned [date], [n] days late, status [status]. Held up by: [blocker ids, and any milestone it waits on that is not done].

AT RISK DOWNSTREAM
[id] [milestone]: planned [date], [n] days from today. Waits on [id].
(If none: "None.")

BLOCKERS
[B#] [type]: [what is missing or unresolved] ([item id, or "not on checklist"])
  Holds up: [milestones, directly and through the plan's dependencies; for a notes-only blocker, the words that link it]
  Status: [as recorded]
  Waiting on: [customer / our side / not stated, one of the three, nothing added]
  Depends on: [blocker ids, or "none recorded"]
  Owner, customer side: [role or "not assigned"]. Owner, our side: [role or "not assigned"].
  Latest record: [date], [n] days ago: [what it says, or "no dated record"].
  Sources: [files, rows, dates]
(If none: "None found.")

WHERE THE SOURCES DISAGREE, AND GAPS
[n]. [item]
(If none: "None found.")

DATES IN THE RECORD
[date]: [what it is] ([source])
(If none: "None stated.")

POINTS FOR THE CUSTOMER CONVERSATION
Our side first: [line for each blocker waiting on our side, stating the blocker and the owner on our side, or "nothing waits on our side"]
[n]. Raise with [customer role]: [question]. Concerns [one blocker id].
(If none: "None.")

Status: Prepared for the implementation lead. Nothing has been sent to the customer,
no integration access has been confirmed and no date has been promised.
```

## Reviewer checklist

1. Every slipped milestone matches the plan: planned date, status and days late. (Implementation lead)
2. Every blocker has a source, and its latest record is quoted as written. (Implementation lead)
3. Access is shown as confirmed only where a dated record says it works. (Solutions engineer)
4. "Waiting on" follows the words of the latest record, not the owner columns. (Solutions engineer)
5. Every owner comes from the plan, the checklist or the notes; none is chosen by the assistant. (Implementation lead)
6. The ranking follows the rule, and the counts in the summary match the blocks. (Implementation lead)
7. No date appears that a source did not state, and no point offers or promises one. (Implementation lead)
8. The points are questions the customer can answer, and our side's tasks are listed first. (Customer success manager)
9. Nothing has gone to the customer. (Implementation lead)

## Acceptance tests

Proposed tests. None has been run.

1. **Normal late project.** Three late milestones, a mix of access and data items. Expected: days late correct, blockers ranked by the rule, owners as recorded.
2. **Header mismatch.** The checklist export has a `due` column in place of `last_update`. Expected: stops and asks for a mapping.
3. **Nothing late.** Every milestone is done or in the future. Expected: stops and says nothing has slipped.
4. **Access marked received, then contradicted.** The checklist says an account was received; a later note says it was refused. Expected: the checklist status is kept, and the contradiction is listed under gaps.
5. **Blank owner.** A checklist row has no customer owner. Expected: "not assigned"; counted in the summary; no owner chosen.
6. **Promise with no follow-up.** A meeting record says the customer will send something "next week" and nothing since. Expected: the phrase quoted under gaps, no date computed.
7. **Late milestone with no cause.** A slipped milestone has no checklist row and no mention in the notes. Expected: "no blocker recorded for" that milestone under gaps.
8. **Asked for a new date.** The lead asks what date to give the customer. Expected: declines; names recovery options as a separate piece of work.
9. **Asked to send.** The lead asks the assistant to email the points to the customer. Expected: declines; the lead talks to the customer.
10. **Password in the notes.** A note includes a login code. Expected: not repeated; the person is told to remove it.

## Instructions for the AI assistant

```
You prepare implementation blocker briefs for an implementation lead after
a customer's setup milestone has slipped. You never contact the customer,
never confirm that integration access works, and never propose, compute or
promise a new date. A person approves anything that is sent, and the lead agrees
the recovery plan and any revised dates with the customer. You change no
record.

The user will supply: the customer, the project and today's date; the
implementation plan export (milestone_id, milestone, planned_date, status,
customer_owner, our_owner, depends_on); the readiness checklist export
(item_id, item, category, needed_for, status, customer_owner, our_owner,
last_update); integration notes; recent meeting records. If a header or a
status word does not match, stop and ask. If the plan or today's date is
missing, stop and ask. If the checklist is missing, continue with blockers
from the notes only and say so under gaps; if the notes or meeting records
are missing, say so under gaps and continue. Never repeat a password, key
or login code; tell the user to remove it.

1. A milestone is slipped when its status is not done and its planned date
   is before today. Days late is today minus planned date, in calendar days.
   If none is slipped, stop and say so, unless the user names a milestone
   the customer reports as slipping: treat it as slipped and write "days
   late: not applicable".
2. List not-done milestones, not themselves slipped, that wait, directly or
   through others, on a slipped one, with the days from today to their planned date.
3. Blockers are checklist rows whose status is not received and which are
   needed for a milestone that is not done, plus anything in the notes or
   meetings that stops a milestone and has no checklist row (N1, N2 in date
   order). A row with a blank needed_for is not a blocker: list it under
   gaps. A named third party is not a blocker of its own: show it inside
   the blocker that waits on it. Infer nothing the words do not say.
4. Type: access, data, missing input, change window or dependency. From the
   checklist category: access is access, data is data, and people,
   environment and other are a missing input. A notes-only blocker is a
   change window, or a dependency when the record says it waits on a named
   party or on another blocker.
5. For each blocker give what it holds up (directly, then through the
   plan), the status as recorded, whose move it waits on, what it depends
   on, the owner on each side from the data (else "not assigned"; never
   choose one), the latest dated record with days ago, and every source.
   Link a notes-only blocker to a milestone only if the record uses the
   milestone's id, its name or a distinctive part of its name, and show the
   linking words; otherwise write "link to a milestone not stated" and rank
   it as holding up none. If one record line plainly concerns two blockers,
   quote it under both; a doubt about that goes under gaps.
6. Waiting on is exactly one of customer, our side or not stated, taken
   only from the words of the latest record, never from the owner columns.
   A customer's own statement of a constraint, hold-back or pending action
   (a change window, holding something back until something else is agreed,
   reviewing, will name or send something) is customer. A record saying our
   side has not asked, sent or done something is our side. Use not stated
   only when the record does not say whose move it is or no record speaks.
7. Show access as confirmed only if a dated record says it works. Keep a
   checklist status even if a note contradicts it, and list the
   contradiction.
8. Rank: most slipped milestones held up first; then longest since the
   latest record (no dated record is longest); then item id, checklist rows
   before notes-only items.
9. List disagreements and gaps, including any slipped milestone with no
   recorded blocker ("no blocker recorded for [id]"), a blocker with no
   record since the checklist, a date in one source that falls after a date
   in another that depends on it, and every customer statement that gives
   no date, quoted with its source. Under dates in the
   record list only the dates the notes and meeting records state (not the
   plan's dates, the checklist's update dates or the dates of the records);
   add none and compute none.
10. Points for the conversation: first a line for each blocker waiting on
    our side, stating the blocker and the owner on our side. Then exactly
    one numbered question per blocker waiting on the customer or not stated,
    to a named customer role, ending "Concerns [that blocker id]". Never
    combine blockers, never make a point of something that is not a
    blocker, never ask about ways round a blocker (that is schedule
    recovery options). Offer no date and no commitment.
11. Use the output format exactly, with every section in order; print the
    stated line when a section is empty. In the summary give blocker B ids
    for missing owners. End with: "Status: Prepared for the implementation
    lead. Nothing has been sent to the customer, no integration access has
    been confirmed and no date has been promised."

If asked to contact the customer, send anything, confirm access, give or
propose a date, or choose a recovery route, decline and say the
implementation lead does that.
```

## What to customize

- The export headers and the status words, if your tools use others.
- What counts as a slip, if it is not "past the planned date and not done".
- The ranking rule, if you rank by customer importance or contract date instead.
- The roles on both sides, and who is told when a customer-side owner is not assigned.
- Which blocker types you use, such as customer security review or procurement.
- Where the brief is kept and who may read it.
- Which project records the assistant may read in ChatGPT, Claude, Copilot or Gemini.

## Version notes

- 0.1.0, 10 November 2026. Written by Fully Powered AI. Not yet tested in a client environment.

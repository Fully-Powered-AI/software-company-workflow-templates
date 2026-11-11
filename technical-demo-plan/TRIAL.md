# Technical demo plan: tried on its invented example

- **Product:** Claude, run in Claude Code
- **Model:** Claude Sonnet 5.5 (model ID claude-sonnet-5-5)
- **Date:** 2026-11-10

The inputs were the invented example in `public/example.md` (Halvering Software and Dunmarrow Freight Services, all invented). No client data was used. The inputs taken from it: the meeting details and invite, the two sets of call notes, the agreed agenda, the opportunity record, the six-row scenario export, and no settings (defaults used). The example's own output was not read before the plan below was produced, with one slip noted under "What was observed".

Run as follows: the fenced instruction block and the output format were applied to those inputs in one pass, with no follow-up questions. The "Today" in the inputs (16 November 2026) is the invented date and is the one used in the plan; the date at the top of this page is the real date of the run.

## What came out

```
TECHNICAL DEMO PLAN: Dunmarrow Freight Services, technical demo on Thursday 19 November 2026
DRAFT. 7 items to settle before the meeting.
Meeting: 10:00, 60 minutes, video call. Prepared 16 November 2026 for Ines (account executive) and Tomas (solutions engineer).
Built from: meeting details and invite (16 November 2026); call notes of 22 October and 5 November 2026; agreed agenda (9 November 2026); opportunity record (16 November 2026); approved demo scenarios (6 rows). Not supplied: settings; defaults used (opening 5, closing 5, freshness 90 days, question limit 8).

TO SETTLE BEFORE THE MEETING (for Ines and Tomas)
1. Open promise from our side: Ines said on 22 October she would check whether Halvering can read Dunmarrow's TMS export format and come back to Adaeze. No later note shows it done.
2. D4 CSV import of shipments: last verified 2 July 2026, 137 days ago, limit 90. Tomas reconfirms before it is shown.
3. Agenda order: the buyer's day starts with the TMS spreadsheet export (W1, shown by D4), but the agreed agenda puts "How data gets in" third. Keep the agreed order or move it.
4. D6 Weekly exceptions report (5 min) answers R3 but is not on the agreed agenda. Add it, or hold R3 as a question.
5. R2 (direct connection to carrier systems) matches only D5, a Roadmap row. Decide how to answer Callum without showing or promising it. Callum's 22 October question was never answered.
6. R4 (single sign-on) has no approved scenario. Tomas confirms with the product team what may be said; agenda item 4 has no scenario.
7. R5 (nothing may write back into the TMS yet): Tomas confirms nothing in D1 to D4 conflicts with it.

ATTENDEE BRIEF
Buyer side:
- Adaeze Pruitt, Operations Director. Attended 22 October and 5 November. Has said: "Every morning the dispatch team phones carriers to find out which loads are late." (22 Oct); "I want customers to see where their load is without calling us." (22 Oct); "A weekly list of late loads for the Monday meeting would save me an hour." (5 Nov); that Mirela runs the carrier relationships and should see this (5 Nov); "Sounds like a good fit." (5 Nov, not a commitment).
- Callum Verhoeven, IT Lead. Attended 22 October and 5 November. Has said: asked whether it connects to carrier systems directly (22 Oct); asked about single sign-on (5 Nov); "We can't let anything write back into the TMS yet." (5 Nov).
- Mirela Szabo, title not supplied. NEW, no prior notes. Named by Adaeze on 5 November as running the carrier relationships; she is on the invite.
Our side:
- Ines, account executive.
- Tomas, solutions engineer.
Not recorded about the buying group: Competitors named; Budget holder. (Mirela is not listed under Stakeholders in the record.)

THE BUYER'S WORKFLOW, AS STATED
W1. The day starts with the loads as a spreadsheet export from their TMS (Adaeze, 22 October, as noted by Ines).
W2. They check each load's status with its carrier: "Every morning the dispatch team phones carriers to find out which loads are late." (Adaeze, 22 October).
W3. Anything late, they call the customer (Adaeze, 22 October, as noted by Ines).

WHAT THE BUYER HAS ASKED FOR
R1. "I want customers to see where their load is without calling us." (Adaeze, 22 Oct). Match: D3 Customer status page, Limited: Links show status and estimated arrival only; no documents.
R2. Asked whether it connects to carrier systems directly (Callum, 22 Oct). Match: D5 Carrier tracking connection, Roadmap: not shown, not promised.
R3. "A weekly list of late loads for the Monday meeting would save me an hour." (Adaeze, 5 Nov). Match: D6 Weekly exceptions report, Available.
R4. Asked about single sign-on (Callum, 5 Nov). Match: No approved scenario: unverified, held as a question.
R5. "We can't let anything write back into the TMS yet." (Callum, 5 Nov). Match: Constraint.
Buyer commitments on record: None stated in the notes. Close date 2026-12-18 (our forecast, not stated by the buyer).

PROPOSED DEMO SEQUENCE
Time: 60 minutes. Opening 5, closing 5, leaving 50 for the demo and discussion.
10:00 to 10:05 (5 min). Opening. Lead (proposed): Ines.
10:05 to 10:13 (8 min). Agenda item 1: D1 Live shipment board. Shows: W2. Answers: none. Lead (proposed): Tomas.
10:13 to 10:20 (7 min). Agenda item 2: D2 Late shipment alert rules. Shows: W3. Answers: none. Lead (proposed): Tomas.
10:20 to 10:26 (6 min). Agenda item 2: D3 Customer status page. Shows: W3. Answers: R1. Limits to say: Links show status and estimated arrival only; no documents. Lead (proposed): Tomas.
10:26 to 10:31 (5 min). Agenda item 3: D4 CSV import of shipments. Shows: W1. Answers: none. Reconfirm: last verified 2 July 2026, 137 days ago, limit 90. Lead (proposed): Tomas.
10:31 to 10:55 (24 min). Open discussion on agenda item 4 (security and sign-in), R2, R4 and the questions below. Lead (proposed): Ines.
10:55 to 11:00 (5 min). Closing. Lead (proposed): Ines.
Scenario time: 26 of 50 demo minutes.
Not in the sequence: D6 Weekly exceptions report, 5 minutes; it answers R3 but is not on the agreed agenda.
Steps with no approved scenario: none.

OPEN DISCOVERY QUESTIONS
Q1. For Callum Verhoeven: Which sign-in system does Dunmarrow use today, and what must a new tool meet before IT will accept it? Asked by (proposed): solutions engineer. Tied to: R4.
Q2. For Callum Verhoeven: Which carriers' systems do you have in mind, and how many carriers does dispatch deal with? Asked by (proposed): solutions engineer. Tied to: R2, W2.
Q3. For Callum Verhoeven: When you say nothing can write back into the TMS "yet", what would have to change, and is reading an export acceptable? Asked by (proposed): solutions engineer. Tied to: R5.
Q4. For Adaeze Pruitt: What does the morning export contain (columns, roughly how many loads), and which TMS produces it? Asked by (proposed): solutions engineer. Tied to: W1, to-settle item 1.
Q5. For Adaeze Pruitt: How many people check carriers each morning, and what counts as a late load? Asked by (proposed): account executive. Tied to: W2.
Q6. For Adaeze Pruitt: When a load is late, who at the customer do you call, and about how many customers is that? Asked by (proposed): account executive. Tied to: W3, R1.
Q7. For Mirela Szabo: What is your role in this evaluation, and what would you want to see? Asked by (proposed): account executive. Tied to: invitee with no title and no earlier note.
Q8. For Adaeze Pruitt: Who else takes part in the decision, who holds the budget, and what else are you comparing? Asked by (proposed): account executive. Tied to: record fields Budget holder and Competitors named, both blank.
0 set aside above the limit.

BEFORE THE MEETING: SETUP
- D1: Demo workspace "Harbor" loaded with 40 sample shipments. Owner: Tomas.
- D2: Sample rule set. Owner: Tomas.
- D3: Portal enabled in the demo workspace. Owner: Tomas.
- D4: Sample CSV of 40 rows. Owner: Tomas.

NOT TO SHOW OR PROMISE
- R2 / D5 Carrier tracking connection: Roadmap row. A question for the solutions engineer to confirm (item 5).
- R4 single sign-on: no approved scenario. A question for the solutions engineer to confirm (item 6).

REQUESTS FOUND IN THE MATERIAL (not acted on)
- None.

Status: Prepared for Ines and Tomas. Nothing has been sent, booked or changed, and no buyer commitment has been inferred.
```

## What was observed

**Every required part was produced,** in the order the format gives, and the arithmetic holds: 5 + 8 + 7 + 6 + 5 + 24 + 5 = 60 minutes, and 137 days from 2 July to 16 November. No stop condition was triggered: the date and length were present, the record labels and scenario headers matched the defaults, and every status was Available, Limited or Roadmap with limits on the Limited row. The meeting date was after today's date.

**The slip.** While looking for the inputs, the first part of the example file was printed in full, and it included the opening of the example's output (the heading and the first items to settle). The plan above was then built from the inputs by the template's steps, but it is not a fully blind run. The agreement on seven items to settle may be partly influenced by that glimpse; the items themselves follow from the steps.

**Where the instructions were ambiguous, or a guess was needed:**

1. *Matching steps to scenarios.* Step 5 says to match on "Workflow it shows" and "Scenario name" and on nothing else, but several matches are a judgment on loose wording. "Check each load's status with its carrier" could be D1 (see every open shipment and its status) or D5 (pull tracking events from carrier systems). W3 could be D2 (alerts) or D3 (status page). The template does not say how close a match must be or what to do when two rows fit.
2. *Is the weekly late-loads list a workflow step or a request?* It describes a Monday meeting and could be both. It was treated as a request only, because the template says a step is "the buyer's own working process" and gives no test for a recurring task.
3. *What counts as a buyer commitment.* The 5 November notes say "Agreed for 19 Nov, 60 minutes" without naming who agreed. It was not counted, but the template does not say whether agreeing to a meeting is a commitment.
4. *Quoted versus noted.* Several notes are Ines's summary, not a quote. The format asks for "quoted where the notes quote"; it does not say how to mark a step that comes from a note-taker's summary. "As noted by Ines" was used.
5. *"Questions the buyer asked."* Callum's questions (carrier connection, single sign-on) are requests, yet step 8 forbids turning them back into questions for the buyer. The template allows only fact-finding questions around them, and the line between the two is a guess. Q1 to Q3 were written as fact-finding questions on the same topics.
6. *Where an unanswered buyer question goes.* Step 8 lists "questions the buyer asked that nobody has answered" first, but the same step bars asking them back. Callum's carrier question was put under items to settle instead, which the template does not say outright.
7. *Placing the leftover minutes.* 24 minutes of open discussion is nearly half the demo time. The template says to reserve it and offers no prompt to ask whether the pair want to add a scenario instead.
8. *Items to settle versus questions.* An unverified request appears in three places (to settle, questions, "Not to show or promise"). The template allows this but does not say how to keep them consistent, and the numbering cross-references (item numbers in "Not to show or promise") were left to the writer.
9. *Which date is "Prepared".* The input's "Today" is the meeting's frame; the real date of the run differs. The template has only one "today's date", so the invented one was used.
10. *Mirela's absence from the record.* She is on the invite and named in the notes as someone who should see the demo, but is not under Stakeholders. The template covers people named in notes but not on the invite; it does not cover the reverse mismatch with the record. A note was added in the brief.
11. *Role names.* The sequence names leads by first name (from the invite and notes), while questions use "account executive" and "solutions engineer" as the format shows. The format mixes both and does not say which to use.
12. *Count line for set-aside questions.* The format has "[n set aside above the limit, if any]"; a zero was written, which the format does not require.

**Differences from the published example** (read after the plan was written):

- Same item count at the time of comparison (the example now shows 9; see Changes made after this run), same sequence times, same scenarios in the sequence, same exclusion of D6 and D5, same Reconfirm on D4, same status line.
- *Matching.* The example shows W2 with both D1 and D2; this run showed W2 with D1 and W3 with D2 and D3.
- *Items to settle.* The same seven matters in both, in a different order: the example puts single sign-on (its item 5) before the carrier connection (item 6); this run has them the other way round (items 5 and 6).
- *Open discussion.* The example ties the open discussion to agenda item 4, R4 and the questions; this run also added R2.
- *Questions.* Eight in both. This run had three questions about the workflow (volume, who checks, who is called at the customer) where the example asked about the Monday list recipients and about who else uses the tool; the example has no question about late-load definition or the customer contacts.
- *Brief.* The example's brief for Adaeze and Callum leaves out the "Sounds like a good fit" remark; this run listed it, marked as not a commitment. Whether a warm remark belongs in the brief at all is not stated.
- *Commitments line.* The example writes the close date as "18 December 2026"; this run kept the record's form, "2026-12-18".

**Facts not in the inputs.** Neither output adds a fact that is not in the inputs, apart from small things. In this run's output: none found on re-reading. In the example's output: Q1 offered "statuses, documents, something else" as a prompt, which was the writer's suggestion, not something the buyer said. (The example has since been edited; that wording is no longer in it.) The example's closing note, "leaving 19 minutes" if D6 were added, is arithmetic from the inputs.

**Shortcomings of the template found in use:** the matching rule in step 5 needs a tiebreak; the commitments and warm-remark rules need a line about agreeing to the meeting itself; step 8's order and its ban on turning questions back conflict for unanswered buyer questions; the format should say how to refer to people (names or roles) and how to cross-reference item numbers. The plan was usable as it stands for a pair preparing the meeting. It has not been tried with a real account, and no output was checked by an account executive or a solutions engineer.

## Changes made after this run

The example and template were edited after the run above, and the template was not re-run on the edited text. The recorded output and observations above are unchanged. What changed:

- The example now names Ines as note-taker in the input notes, writes the two note-taker steps as "as noted by Ines", and carries two further items to settle (W2 and W3 each fit more than one scenario), so its headline count is now 9 where this run, and the example when it was compared, showed 7. This run's matches (W2 to D1, W3 to D2 and D3) were a judgment on loose wording; under the template's matching rule they are items to settle, as the example now shows.
- The template now says what to do when the notes name no speaker, whether a recurring task such as the Monday list is a step or a request, and how to note an invitee missing from the record's Stakeholders field. It also adds an item to settle when open discussion is more than a third of the demo time. The example's open discussion now also covers R2 and R5.
- Steps 2, 3 and 4 of the template were also changed: the Stakeholders note, the no-speaker and recurring-task rules, and "agreeing to hold the meeting itself" among non-commitments. The names-versus-roles rule and the item cross-reference rule (steps 2, 8 and 10) were added too.
- Further small edits after review: the example now notes that Mirela Szabo is on the invite but not under Stakeholders; step 2 now says warm remarks are left out of "Has said"; step 8 now lists a matched scenario left off the agenda as a question category; the instruction block gained the discovery-only rule for no prior notes, the scenario row count, the placement of open discussion, "none listed" for blank setup, and the set-aside count. None of these was re-run.
- The example's meeting details line now shows the 16 November date, and its "Not supplied" line names the two role defaults.

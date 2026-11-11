# Technical demo plan: an invented example

*Illustrative example with invented data.* Halvering Software, Dunmarrow Freight Services and every person in this example are invented. Halvering is a small company that sells shipment tracking and late-load alerts to freight forwarders. Ines, its account executive, and Tomas, its solutions engineer, have a technical demo with Dunmarrow booked for Thursday 19 November 2026 and prepare on Monday 16 November 2026.

The inputs come first, complete, exactly as Ines and Tomas supplied them. The plan follows.

## What they supplied

**1. The meeting**

```
MEETING
Today: Monday 16 November 2026
Buyer: Dunmarrow Freight Services
Type: technical demo
When: Thursday 19 November 2026, 10:00, 60 minutes, video call
Invited (from the calendar invite):
  Adaeze Pruitt, Operations Director
  Callum Verhoeven, IT Lead
  Mirela Szabo (no title on the invite)
From our side: Ines (account executive), Tomas (solutions engineer)
Stage: technical evaluation
```

**2. Prior call notes**

```
22 Oct 2026, discovery call. Notes by Ines. Ines; Adaeze Pruitt and Callum Verhoeven (Dunmarrow).
- Adaeze: "Every morning the dispatch team phones carriers to find out which loads are late."
- The day starts with the loads as a spreadsheet export from their TMS (transport management system). They check each load's status with its carrier. Anything late, they call the customer.
- Adaeze: "I want customers to see where their load is without calling us."
- Callum asked: does it connect to carrier systems directly? Not answered on the call.
- Ines said she would check whether Halvering can read their TMS export format and come back to Adaeze.

5 Nov 2026, call. Notes by Ines. Ines and Tomas; Adaeze and Callum.
- Adaeze: "A weekly list of late loads for the Monday meeting would save me an hour."
- Adaeze: "Mirela runs the carrier relationships; she should see this."
- Callum asked about single sign-on.
- Callum: "We can't let anything write back into the TMS yet."
- Adaeze: "Sounds like a good fit."
- Tomas offered a technical demo. Agreed for 19 Nov, 60 minutes.
```

**3. The agreed agenda** (sent by Ines on 9 November 2026)

```
1. Walk through your day with our shipment board.
2. Alerts and customer visibility.
3. How data gets in.
4. Questions on security and sign-in.
```

**4. The opportunity record** (fields pasted on 16 November 2026)

```
Account: Dunmarrow Freight Services
Stage: Technical evaluation
Owner: Ines
Close date: 2026-12-18
Stated need: Fewer morning carrier calls; customer visibility
Stakeholders: Adaeze Pruitt (Operations Director); Callum Verhoeven (IT Lead)
Competitors named:
Budget holder:
```

**5. The approved demo scenarios** (export, six rows)

```
Scenario ID,Scenario name,Workflow it shows,Product area,Minutes,Setup needed,Status,Limits,Last verified,Owner
D1,Live shipment board,See every open shipment and its status in one place,Shipment board,8,"Demo workspace ""Harbor"" loaded with 40 sample shipments",Available,,2026-10-20,Tomas
D2,Late shipment alert rules,Set a rule that flags a shipment running late and who is told,Alerts,7,Sample rule set,Available,,2026-10-20,Tomas
D3,Customer status page,Share a read-only status link with a customer,Customer portal,6,Portal enabled in the demo workspace,Limited,Links show status and estimated arrival only; no documents,2026-10-27,Tomas
D4,CSV import of shipments,Load shipments from a spreadsheet,Imports,5,Sample CSV of 40 rows,Available,,2026-07-02,Tomas
D5,Carrier tracking connection,Pull tracking events from carrier systems automatically,Integrations,10,,Roadmap,,2026-10-27,Product team
D6,Weekly exceptions report,Export a weekly list of late and held shipments,Reports,5,Report template loaded,Available,,2026-10-13,Tomas
```

**6. Settings:** none supplied; defaults used.

## The plan

```
TECHNICAL DEMO PLAN: Dunmarrow Freight Services, technical demo on Thursday 19 November 2026
DRAFT. 9 items to settle before the meeting.
Meeting: 10:00, 60 minutes, video call. Prepared 16 November 2026 for Ines (account executive) and Tomas (solutions engineer).
Built from: meeting details and invite (16 November 2026); call notes of 22 October and 5 November 2026; agreed agenda (sent 9 November 2026); opportunity record fields (pasted 16 November 2026); approved demo scenarios (6 rows, last verified between 2 July and 27 October 2026). Not supplied: settings; defaults used (opening 5 minutes, closing 5 minutes, scenario freshness 90 days, question limit 8, product answers from the product team, price and terms from the sales lead).

TO SETTLE BEFORE THE MEETING (for Ines and Tomas)
1. Open promise from our side: on 22 October Ines said she would check whether Halvering can read Dunmarrow's TMS export format and come back to Adaeze. No later note shows it done. Ines answers before the meeting; see Q4.
2. Scenario D4 (CSV import of shipments) was last verified on 2 July 2026, 137 days ago; the limit is 90. Tomas reconfirms it before it is shown.
3. Agenda order: the agreed agenda puts how data gets in (D4, serving W1) third, while W1 is where the buyer's day begins. Ines and Tomas keep the agreed order or move it.
4. R3, the weekly late-loads list, matches D6 (5 minutes) but is not on the agreed agenda. Ines and Tomas add D6, which would leave 19 minutes for discussion, or hold it as Q5.
5. R4, single sign-on, matches no approved scenario. Tomas confirms with the product team what can be said about sign-in before the meeting.
6. R2, a direct connection to carrier systems, matches only the Roadmap scenario D5. Ines and Tomas decide how to answer Callum without showing or promising it.
7. R5, Callum's constraint that nothing writes back into the TMS. Tomas confirms that nothing in D1 to D4 conflicts with it.
8. W2, checking each load's status with its carrier, fits more than one row: D1 (Live shipment board), D2 (Late shipment alert rules) and, on its wording about carrier systems, D5 (Roadmap: not shown, not promised). The plan shows D1 and D2 against W2 provisionally. Tomas chooses which of D1 and D2 serves W2, and Ines and Tomas confirm that D5 stays out.
9. W3, calling the customer about anything late, fits D2 (who is told) and D3 (Customer status page) on loose wording. The plan shows D2 and D3 against W3 provisionally. Tomas chooses which serves W3.

ATTENDEE BRIEF
Buyer side:
- Adaeze Pruitt, Operations Director. Attended 22 October and 5 November. Has said: "Every morning the dispatch team phones carriers to find out which loads are late." (22 October); "I want customers to see where their load is without calling us." (22 October); "A weekly list of late loads for the Monday meeting would save me an hour." (5 November); "Mirela runs the carrier relationships; she should see this." (5 November).
- Callum Verhoeven, IT Lead. Attended 22 October and 5 November. Has said: asked whether it connects to carrier systems directly (22 October); asked about single sign-on (5 November); "We can't let anything write back into the TMS yet." (5 November).
- Mirela Szabo, title not supplied. NEW, no prior notes. Named by Adaeze on 5 November as running the carrier relationships. On the invite but not under Stakeholders in the record; not added.
Our side:
- Ines, account executive.
- Tomas, solutions engineer.
Not recorded about the buying group: Competitors named; Budget holder.

THE BUYER'S WORKFLOW, AS STATED
W1. The day starts with the loads as a spreadsheet export from their TMS (as noted by Ines, 22 October).
W2. Check each load's status with its carrier; "Every morning the dispatch team phones carriers to find out which loads are late." (Adaeze, 22 October).
W3. Call the customer about anything late (as noted by Ines, 22 October).

WHAT THE BUYER HAS ASKED FOR
R1. "I want customers to see where their load is without calling us." (Adaeze, 22 October). Match: D3 Customer status page, Limited: Links show status and estimated arrival only; no documents.
R2. Asked whether it connects to carrier systems directly (Callum, 22 October). Match: D5 Carrier tracking connection, Roadmap: not shown, not promised.
R3. "A weekly list of late loads for the Monday meeting would save me an hour." (Adaeze, 5 November). Match: D6 Weekly exceptions report, Available.
R4. Asked about single sign-on (Callum, 5 November). Match: No approved scenario: unverified, held as a question.
R5. "We can't let anything write back into the TMS yet." (Callum, 5 November). Match: Constraint.
Buyer commitments on record: None stated in the notes. The record's close date, 18 December 2026, is our forecast, not stated by the buyer.

PROPOSED DEMO SEQUENCE
Time: 60 minutes. Opening 5, closing 5, leaving 50 for the demo and discussion.
10:00 to 10:05 (5 min). Opening. Lead (proposed): Ines.
10:05 to 10:13 (8 min). Agenda item 1: D1 Live shipment board. Shows: W2 (candidate, item 8). Answers: none. Lead (proposed): Tomas.
10:13 to 10:20 (7 min). Agenda item 2: D2 Late shipment alert rules. Shows: W2 and W3 (candidate, items 8 and 9). Answers: none. Lead (proposed): Tomas.
10:20 to 10:26 (6 min). Agenda item 2: D3 Customer status page. Shows: W3 (candidate, item 9). Answers: R1. Limits to say: Links show status and estimated arrival only; no documents. Lead (proposed): Tomas.
10:26 to 10:31 (5 min). Agenda item 3: D4 CSV import of shipments. Shows: W1. Answers: none. Reconfirm: last verified 2 July 2026, 137 days ago, limit 90. Lead (proposed): Tomas.
10:31 to 10:55 (24 min). Open discussion on agenda item 4 (security and sign-in), R2, R4, R5 and the questions below. Lead (proposed): Ines.
10:55 to 11:00 (5 min). Closing. Lead (proposed): Ines.
Scenario time: 26 of 50 demo minutes.
Not in the sequence: D6 Weekly exceptions report, 5 minutes; it matches R3 but is not on the agreed agenda (item 4 above).
Steps with no approved scenario: none.

OPEN DISCOVERY QUESTIONS
Q1. For Callum Verhoeven: When you ask about connecting to carrier systems directly, which carriers do you mean, and what do you need from them? Asked by (proposed): Tomas. Tied to: R2.
Q2. For Callum Verhoeven: Which sign-in method does Dunmarrow use for its other business systems, and what must a new system meet to pass your review? Asked by (proposed): Tomas. Tied to: R4.
Q3. For Callum Verhoeven: You said nothing can write back into the TMS yet. Does that cover only the evaluation, or what you expect later too? Asked by (proposed): Tomas. Tied to: R5.
Q4. For Adaeze Pruitt: What does the TMS export hold: which columns, how many loads a day, and who produces it? Asked by (proposed): Tomas. Tied to: W1 and to-settle item 1.
Q5. For Adaeze Pruitt: Who receives the Monday late-loads list, and which loads and details does it show? Asked by (proposed): Ines. Tied to: R3.
Q6. For Mirela Szabo: What is your part in this evaluation, and which of the morning carrier checks are yours? Asked by (proposed): Ines. Tied to: invitee with no title and no earlier note.
Q7. For Adaeze Pruitt: Besides the three invited, who will use this every day or approve it? Asked by (proposed): Ines. Tied to: record field Budget holder, blank.
Q8. For Adaeze Pruitt: Which other ways of solving this have you looked at, if any? Asked by (proposed): Ines. Tied to: record field Competitors named, blank.

BEFORE THE MEETING: SETUP
- D1: Demo workspace "Harbor" loaded with 40 sample shipments. Owner: Tomas.
- D2: Sample rule set. Owner: Tomas.
- D3: Portal enabled in the demo workspace. Owner: Tomas.
- D4: Sample CSV of 40 rows. Owner: Tomas.

NOT TO SHOW OR PROMISE
- D5 Carrier tracking connection (R2): Roadmap row. Not shown, not promised; a question for Ines, Tomas and the product team to settle (item 6).
- R4 single sign-on: no approved scenario. Only a question for Tomas to confirm (item 5).

REQUESTS FOUND IN THE MATERIAL (not acted on)
- None.

Status: Prepared for Ines and Tomas. Nothing has been sent, booked or changed, and no buyer commitment has been inferred.
```

The two matching items, 8 and 9, come from the matching rule: W2 fits D1, D2 and, on its wording, the Roadmap row D5, and W3 fits D2 and D3, so the plan names every candidate and leaves the choice to Tomas. The nine items are: the open promise (1), the stale scenario (2), the agenda order (3), D6 (4), single sign-on (5), the carrier connection (6), the write-back constraint (7), W2 (8) and W3 (9). Every line of the plan traces to the notes, the invite, the agreed agenda, the record or the scenario export above. The demo time is 60 − 5 − 5 = 50 minutes; the four scenarios in the sequence take 8 + 7 + 6 + 5 = 26, leaving 50 − 26 = 24 for open discussion. Adding D6 would leave 24 − 5 = 19. D4 was last verified 137 days before 16 November 2026.

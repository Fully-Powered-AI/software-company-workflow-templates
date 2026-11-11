# Trying "Usability test session plan" on its invented example

- **Product:** Claude, run in Claude Code
- **Model:** Claude Sonnet 5.5 (model ID claude-sonnet-5-5)
- **Date:** 2026-11-10

The inputs are the invented example in `public/example.md` (Fenlow Rota, a made-up company and prototype). No client data was used. The template is `member/template.md`, version 0.1.0, as revised after a first run and an independent review, and again after a second run and a second independent review (see "Changed before this run"). The inputs used were the six screens P1 to P6, three questions Q1 to Q3, five participant criteria (U1 to U3, M1, M2), two pain points K1 and K2, the constraints, and the handling already decided, all as written in the example. This is a third run, one pass with no retries.

One thing to know about how fair this trial is: this run was made by the same session that revised the template, after reading the earlier record and the reviewer's points. I followed the revised instruction block and output format on the inputs, but my output is not independent of the template's revisions or of the earlier runs, and the example's plan was then set to the output below so that the two agree.

## What came out

```
USABILITY TEST SESSION PLAN: Ask a colleague to cover a shift (Fenlow Rota prototype)

Prepared for: the product owner. Method and recruitment approved by: the research lead (not yet approved).
Plan covers: 3 questions, 3 tasks, 2 groups, 8 sessions, Monday 16 to Friday 27 November 2026.
Inputs read: 6 screens (P1 to P6), 3 questions (Q1 to Q3), 5 participant criteria (U1 to U3, M1, M2), 2 pain points (K1, K2). Not supplied: success targets.

What is tested: the clickable prototype for asking a colleague to cover a shift, screens P1 to P6.
Not tested: nothing is stated as out of scope.

Questions to answer:
Q1. Can a staff member find out how to ask a colleague to cover a shift, without help?
Q2. Do people understand who has to accept and who has to approve?
Q3. Can a shift manager find and deal with a waiting request?
Questions a task cannot answer: None.

Participants:
Group G1, shop and cafe staff, 5 sessions (R01 to R05, default). Must have: U1, U2.
Group G2, shift managers, 3 sessions (R06 to R08, default). Must have: U3.
Everyone, must not have: M1, M2.
Screening questions (a person asks these; each is open
and does not reveal which answer qualifies):
- U1. "Where do you work, and how many shifts do you usually work in a week?" Qualifies: a shop or cafe, and three or more a week.
- U2. "Tell me about the last time you needed to change a shift. When was that, and how did you go about it?" Qualifies: a change within the last three months, by any means.
- U3. "On your team, who decides whether people can change shifts?" Qualifies: the person says they do.
- M1. "What field do you work in?" Disqualifies: software, design or user research.
- M2. "What, if anything, have you seen or heard about the new design of this app?" Disqualifies: the person describes having seen a preview.
Criteria that cannot be checked by a question: None.
Total sessions: 8.

Session plan:
Group G1: 40 minutes. Introduction and consent 5 (default); T1 5 (default cap); T2 5 (default cap); wrap-up 5 (default). Planned 20 of 40 minutes (50%; limit 75%, default). Unused: 20.
Group G2: 40 minutes. Introduction and consent 5 (default); T3 5 (default cap); wrap-up 5 (default). Planned 15 of 40 minutes (37.5%; limit 75%, default). Unused: 25. This is under half the session: see O5.
Booked time: 8 sessions x 40 minutes = 320 minutes.
The end-of-task questions (N6) are not in the caps; they use the unused minutes.
Before the first session: one practice run of the whole session with a colleague
who is not on the product team, to check the timing and the wording of the tasks.

Tasks:
T1 [G1; answers Q1; pain point K1]
  Starts at: P1.
  Say to the participant: "You can't work one of your upcoming shifts. Get a colleague to take it instead."
  Done when: the participant has sent the request to a colleague and the confirmation screen (P5) is showing.
  Expected path: P1, P2, P3, P4 (optional), P5.
  Time cap: 5 minutes (default).
  Depends on: nothing.
  Needs prepared: an upcoming shift on P1 (see O2).
T2 [G1; answers Q2; pain point K2]
  Starts at: P5, where T1 ends (see O7).
  Say to the participant: "Find out where things stand with the arrangement you just made." Then, once they answer: "In your own words, what happens next, and who is involved?"
  Done when: the participant has said where things stand and has answered the second question.
  Expected path: P5, and P1 if they go to it.
  Time cap: 5 minutes (default).
  Depends on: T1. If T1 was not completed, see O1.
  Needs prepared: the request sent in T1 (see O1).
T3 [G2; answers Q3]
  Starts at: P6.
  Say to the participant: "A colleague has agreed to take over one of your team's shifts, and it needs your decision. Deal with it the way you would in a normal week."
  Done when: the participant has pressed "Approve" or "Decline" on the waiting row.
  Expected path: P6.
  Time cap: 5 minutes (default).
  Depends on: nothing.
  Needs prepared: P6 showing one waiting row (see O2). The way a manager reaches P6 is not described (see O3).
Task wording check: labels and screen names checked, from the screens. On-screen text: "Shifts" (P1 title), "Waiting for [name]" (P1), "Request swap", "Who can cover?" (P3 title), "Send", "Request sent. Waiting for [name] to accept. Your manager approves it after." (P5), "Pending swaps" (P6 title), "Approve", "Decline". Screen names given by the owner, not on-screen text: "Staff home", "Shift detail", "Colleague picker", "Optional note", "Confirmation", "Manager view". No task contains "swap", "request", "cover", "send", "waiting", "accept", "manager", "pending", "approve" or "decline". Two words match: "shift" or "shifts" (T1 and T3), which is also part of the P1 title and the P2 name, and "colleague" (T1 and T3), which is part of the P3 name. Both are the product's ordinary subject matter, so they are kept; the product owner is asked to confirm (O4).

Neutral prompts (the facilitator uses these words and no others):
N1. Opening: "We are testing the design, not you.
Nothing you do is wrong, and you can stop at any time."
N2. Thinking aloud: "Please say out loud what you are looking at
and what you are thinking as you go."
N3. Silence of 20 seconds or more: "What are you thinking right now?"
N4. Asked "Is this right?": "What would you expect to happen?"
N5. Asked "What do I do?": "What would you do if I weren't here?"
N6. End of each task, in this order: "On a scale from 1, very hard, to 5,
very easy, how easy was that?" and then "How did that go?" and then
"Was anything unclear?"
N7. Wrap-up: "Is there anything else you would like to say?"
Help rule: help is anything said beyond prompts N1 to N7. Level 0, none. Level 1, the facilitator repeats the task wording, which counts as help. Level 2, only after the participant has made no progress for 2 minutes (default) or the cap is reached, the facilitator says "Let's move on to the next one" (on the last task of the session, "Let's stop here") and the task is marked Not completed. Any help is written in the notes with the step it was given at.

Observation note template (one set for each participant and task; blank):
- Participant ID and group:
- Task:
- Starting screen reached (yes or no):
- Path taken, screen by screen:
- Result (Completed unaided, Completed with help, Not completed, Stopped by participant):
- Time taken, in minutes and seconds:
- Wrong turns (screens opened that are not on the expected path), counted:
- Help given and at which step:
- Ease rating, 1 (very hard) to 5 (very easy), asked in N6:
- Exact words said, in quotation marks:
- What happened, described without interpretation:
- Answer to the second question in T2, written as said (T2 only):
- Question it bears on (Q1, Q2 or Q3):

Success measures:
- Completed unaided: done condition met with no help.
- Completed with help: done condition met after level 1 help.
- Not completed: done condition not met by the cap.
- Stopped by participant: the participant asks to end the task or the session
  before the done condition is met or the cap is reached. Counted apart from
  Not completed.
- Time on task, wrong turns, ease rating: as recorded in the notes.
- Q2 only, counted from the participant's own words (default scale): Names both the colleague accepting and the manager approving, Names one of them, or Names neither.
- T1: counts for Q1. T2: counts for Q2. T3: counts for Q3.
Targets: Not set. The product owner sets one for each task before the first session; the plan does not supply them.

Decisions to settle before recruiting:
D1. Recording (none, audio, screen and audio, or video and screen): Not decided. Owner: research lead.
D2. Consent wording: the company's own form, owned by the research lead. This plan does not write or judge it.
D3. Who may see notes and recordings, and how long they are kept: Not decided. Owner: research lead.
D4. Test data: the prototype uses made-up accounts, as supplied.
D5. Names in notes: participant IDs only (default).
The list linking IDs to names is kept apart by the research lead.
D6. Incentive for participants: Not decided. Owner: product owner.
D7. Language and access needs: English only, as supplied.

Coverage:
Questions: Q1, T1. Q2, T2. Q3, T3 in part (the plan has no task that starts before P6, because how a manager reaches P6 is not described; see O3).
Pain points: K1, T1. K2, T2.
Screens: P1, T1 (T2 if they go to it). P2, T1. P3, T1. P4, T1. P5, T1, T2. P6, T3.
No task: None.
Conflicts between inputs: None.

Open questions: 7.
O1. T2 starts from a request already sent. If T1 is not completed, does the prototype have a prepared state to start T2 from? Owner: product owner.
O2. T1 needs a test account with an upcoming shift on P1, and T3 needs P6 to show one waiting row. Will the prototype be set up that way? Owner: product owner.
O3. Q3 asks whether a manager can find a waiting request, but the inputs do not describe how a manager reaches P6, so T3 starts there and covers Q3 only in part. How does a manager get to P6, and should T3 start earlier? Owner: product owner.
O4. T1 and T3 use the word "shift", which is also part of the P1 title and the P2 name, and the word "colleague", which is part of the P3 name. Are they acceptable as ordinary subject matter, or should the tasks avoid them? Owner: product owner.
O5. G2 sessions use 15 of 40 minutes. Should the managers also do T1 or T2, or should the sessions be shorter? Owner: research lead.
O6. What result on each task would count as good enough? Owner: product owner.
O7. T2 starts on P5, which already says who accepts and who approves, so T2 may measure memory of that text more than understanding. Should T2 start from a different state, such as P1 with a request already sent? Owner: research lead.

Approvals (left empty):
Research lead approves method and recruitment: ____________
Product owner confirms what is tested: ____________

Every line traces to the inputs supplied, except the items marked (default).
This plan holds no participant findings.
It recruits nobody, contacts nobody and judges no design.
```

## What was observed

Every part of the output format was produced, and the arithmetic came out as the template's own acceptance test 1 predicts (50% and 37.5%, booked time 320 minutes). Nothing made the template stop: the prototype and questions were supplied, no participant data was pasted in, and nothing asked for a password. The only defaults used were the ones the inputs left open (introduction, wrap-up, task cap, 75% limit, 20 seconds of silence, 2 minutes without progress, participant IDs and the three-way scale for counting the understanding answer).

What the revised template handled this time: open screening questions with no yes or no; a wording check that lists every label and the one matching word; fixed wording for the ease rating inside N6; a starting-screen check that led to Q3 being covered in part; prepared data for T1 and T3 asked for in O2; a definition of Stopped by participant; and the end-of-task time taken from the unused minutes.

Where the instructions were still ambiguous or I had to guess:

- **Order inside N6.** The template now fixes the order (rating, then "How did that go?", then "Was anything unclear?"). I followed it. Whether asking for the rating first changes the answers is not something the template or this run can say.
- **Words kept as subject matter.** "Shift" appears in T1 and T3 and in the P1 title and the P2 name; "colleague" appears in T1 and T3 and in the P3 name, which is a screen name, not on-screen text. The template says to reword if it can be. I judged that these tasks cannot be worded without the words, kept them and asked in O4. That is a judgement the template leaves to the model and the owner.
- **A task that follows another.** T1 ends on P5, whose text states who accepts and who approves. The revised template says a following task starts where the earlier one ends, so I started T2 on P5, and that the task may then measure memory of that text more than understanding, so I raised it as O7. It does not say what the better start would be; that stays with the research lead.
- **How the participant sees things remotely.** The inputs say remote on a phone browser. The template has no field for how the facilitator will see the participant's screen; recording and screen sharing sit in D1 only.
- **Where G2's extra time goes.** The template asks whether to add something or shorten (O5) but gives no way for the plan to propose anything. This is as designed.
- **Level 2 wording.** "Let's stop here" on the last task is a second fixed phrase. The template says which task it applies to, and I applied it to the last task in each group's session (T2 for G1, T3 for G2) without printing that mapping in the plan.
- **Prepared data.** The inputs say the prototype uses made-up accounts, which settles test data but not what the accounts hold. I asked in O2 rather than assume.
- **The scale for the understanding answer** is the template's default and is marked (default) in the plan. It is not from the inputs.

Facts in the output that are not in the inputs: the participant IDs R01 to R08 and the three-way scale, both marked (default). The percentages and totals follow from the inputs and defaults. The two facts the first run's plan carried that were not in the inputs ("Thursday evening" in two tasks, and the sentence in D4 about participants not entering their own details) are gone.

I did not check this trial against a third run. It shows that one pass by one model on one invented case produced all the required parts. It is not a test in a real environment.

## Changed before this run

The first and second runs (also on 10 November 2026) were each replaced by a later record at the author's direction after an independent review; their output is not kept. The review and the first run's own notes led to these changes, made before the run recorded above:

- **Screening questions.** Step 3 now says a screening question is open and that a yes-or-no question naming the criterion is not neutral. The example's U2, M1 and M2 were yes or no questions; they are now open.
- **The wording check.** Step 4 now requires listing every label checked and every task word that matches one, and says how to treat a word that is both subject matter and a label (reword, or keep and ask the product owner). The first example's check missed "cover", which is in the P3 title.
- **The ease rating.** N6 now carries fixed wording for the rating, so asking it does not count as help. The output format, the procedure, the instruction block and the example all carry it.
- **Starting screens.** Step 4 now asks for the data a starting screen must hold ("Needs prepared") and for a check of whether the starting screen can answer the question; a "find" question answered from the screen that shows it is covered in part, and coverage says so.
- **Participant IDs.** The default is R01, R02 and so on, so they do not collide with screen labels.
- **Stopped by participant** is now defined in the success measures. Level 2 has its own words for the last task ("Let's stop here").
- **The understanding scale** (names all, some, none) is now a named default, marked (default) where it is used.
- **Time.** The end-of-task questions are stated to take their time from the unused minutes.
- **Facts not in the inputs.** The example no longer says "Thursday evening", and the sentence about participants not entering their own details is cut from D4.
- **Smaller edits.** The example's input is labelled "Participant criteria" as the template asks, and a trailing space in the output format is removed.

Second review, and the changes made before this third run:

- **Screen names.** The wording check now lists screen names the owner gave, as well as on-screen text. The second plan's check listed "Shift detail" as a label and missed "colleague", which is in the P3 name; it also said "shift" was in every task, but T2 does not contain it.
- **Dependent tasks.** A task that follows another now starts where the earlier one ends, and a later task whose question a just-seen screen already answers raises an open question. T2 used to start on P1, although T1 ends on P5.
- **Smaller edits.** The instruction block's line wrapping is evened out. D7 no longer carries a line about asking for an adjustment, which the output format does not have.

Changed after the run recorded above, and not run again: none.

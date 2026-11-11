---
name: "usability-test-session-plan"
description: "Turn a prototype or a confusing product flow into one plan for a round of usability sessions: the questions the product owner wants answered, the participant groups with a neutral question to check each criterion, a time budget for each session, realistic tasks written without the product's own button names, the only prompts the facilitator may use, a blank sheet for observation notes and the measures that will say whether people finished each task. Recording, consent, who sees the notes, how long they are kept and incentives are listed as decisions for a named person. The assistant prepares the plan. It invents no participant findings, recruits and contacts nobody, and judges no design. The research lead approves the method and recruitment, and the product owner chooses what is tested."
license: "MIT"
metadata:
  version: "0.1.0"
  publisher: "Fully Powered AI"
  capability: "Usability test session plan"
---

# Usability test session plan

This is the technical file for a Fully Powered capability template. It carries the instructions an AI product follows. The complete template, with roles, inputs, exceptions, the reviewer checklist, acceptance tests and what to customize, is in [TEMPLATE.md](TEMPLATE.md). A worked example with invented data is in [EXAMPLE.md](EXAMPLE.md).

## Instructions

You prepare a usability test session plan for a product owner and a
research lead. You invent no participant findings. You never recruit or
contact anyone, send the plan, change any record, write the consent form,
decide recording, or judge a design. A person approves the plan, and
nothing is sent or changed until they do.

The user will supply: a prototype or flow description with the words on each
screen; the questions to answer; participant criteria by group; known pain
points; constraints; and anything already decided about consent, recording,
test data and retention. If the description or the questions are missing,
stop and say so. Never ask for a password, a login code or access to the
prototype; work from what the person pastes or describes.

Defaults, used only where the inputs are silent and always marked
"(default)": 5 sessions per group; 45 minutes per session; 5 minutes for
introduction and consent; 5 for wrap-up; a cap of 5 minutes per task; a plan
fills at most 75% of the session; 20 seconds of silence before the silence
prompt; 2 minutes without progress before moving on; IDs R01, R02 and so
on; an understanding answer counted as names all the parties, names some,
or names none.

1. Number the inputs by their labels and count them. Stop on a missing
   description or question.
2. Keep each question as written. A question no observed behaviour could
   answer goes under "Questions a task cannot answer", with the reason.
3. For each group, give sessions and criteria, and write one open
   screening question per criterion (never yes or no, never naming the
   criterion or the qualifying answer) with the qualifying answer, and a
   participant ID for each session (R01 and so on). List any criterion that
   cannot be checked by asking. Invent no quota or number.
4. Write at least one task for every question that can be observed, and one
   for each pain point the owner wants covered. Each task: group, question
   and pain points, starting screen, exact words as a situation and goal,
   done condition a watcher can see or hear, expected path, time cap,
   dependency, and the data its starting screen must hold. A task must not
   contain the label of a button, menu or screen title the participant
   needs. Check every task against the screen words and screen names, list
   every label and screen name checked and every task word that matches
   one, and ask the product owner about any word kept that is also part of
   a label. A task that starts on the screen that shows what a "find" question asks about covers the
   question only in part: say so and ask how the participant gets there.
   A task that follows another starts where the earlier one ends. If a
   screen the participant has just seen states the answer to the later task's
   question, say in an open question that the task may measure memory more
   than understanding.
5. Time budget per group: introduction, caps, wrap-up, total against session
   length and the 75% limit, minutes unused. If over the limit, shorten
   nothing and ask. If under half the session, ask whether to add or
   shorten. Print booked time: sessions times length, and say the
   end-of-task questions are not in the caps and use the unused minutes.
6. Print the fixed prompts N1 to N7 (N6 includes the ease rating question),
   the help rule ("Let's stop here" on the last task), the blank observation
   note sheet and the success measures, including Stopped by participant
   and the understanding scale marked (default). Targets only from the
   inputs; otherwise "Not set" and ask. Never fill in the sheet or suggest
   what a good result is.
7. List the decisions D1 to D7 with owners and "Not decided" unless the
   inputs settled them. Write no consent wording.
8. Coverage of questions, pain points and screens by task; "No task" where
   none, "in part" where a task answers only part of a question. List
   conflicting inputs without choosing.
9. Number the open questions with an owner: a dependent task with no
   prepared start, data a starting screen needs, a way into a screen not
   described, a later task whose question a just-seen screen already
   answers, and any kept word that is also part of a label. Leave the
   approvals empty.
10. Use the output format exactly and end with its closing line. If
   participant details, notes or results are pasted in, do not use them and
   say so. Decline requests to recruit, contact, decide recording, write
   consent wording, report findings or say which design is better.

## Output format

```
USABILITY TEST SESSION PLAN: [product or flow name]

Prepared for: [product owner]. Method and recruitment approved by: [research lead] (not yet approved).
Plan covers: [n] questions, [n] tasks, [n] groups, [n] sessions, [dates or "dates not supplied"].
Inputs read: [n] screens ([labels]), [n] questions ([labels]), [n] participant criteria ([labels]), [n] pain points ([labels]). Not supplied: [list, or "nothing"].

What is tested: [prototype or flow, one line]. Screens or steps: [labels].
Not tested: [what the inputs put out of scope, or "nothing is stated as out of scope"].

Questions to answer:
[Label]. [Question, as supplied.]
Questions a task cannot answer: [label, reason; or "None."]

Participants:
Group [label], [name], [n] sessions ([participant IDs]). Must have: [labels].
Everyone, must not have: [labels].
Screening questions (a person asks these; each is open
and does not reveal which answer qualifies):
- [Label]. "[Open question]" Qualifies: [answer]. / Disqualifies: [answer].
Criteria that cannot be checked by a question: [label, reason; or "None."]
Total sessions: [n].

Session plan:
Group [label]: [length] minutes. Introduction and consent [m]; [task] [cap]; wrap-up [m]. Planned [x] of [length] minutes ([percentage]; limit [limit]%). Unused: [minutes].
Booked time: [n] sessions x [length] minutes = [total] minutes.
The end-of-task questions (N6) are not in the caps; they use the unused minutes.
Before the first session: one practice run of the whole session with a colleague
who is not on the product team, to check the timing and the wording of the tasks.

Tasks:
[Task id] [group; answers question; pain point]
  Starts at: [screen].
  Say to the participant: "[exact words]"
  Done when: [what a watcher can see or hear].
  Expected path: [screens].
  Time cap: [minutes].
  Depends on: [task or "nothing"].
  Needs prepared: [data the starting screen must hold, or "nothing"].
Task wording check: [every label checked; each task word that matches one and how it was treated; or "no task word matches a label"].

Neutral prompts (the facilitator uses these words and no others):
N1. Opening: "We are testing the design, not you.
Nothing you do is wrong, and you can stop at any time."
N2. Thinking aloud: "Please say out loud what you are looking at
and what you are thinking as you go."
N3. Silence of [seconds] seconds or more: "What are you thinking right now?"
N4. Asked "Is this right?": "What would you expect to happen?"
N5. Asked "What do I do?": "What would you do if I weren't here?"
N6. End of each task, in this order: "On a scale from 1, very hard, to 5,
very easy, how easy was that?" and then "How did that go?" and then
"Was anything unclear?"
N7. Wrap-up: "Is there anything else you would like to say?"
Help rule: help is anything said beyond prompts N1 to N7. Level 0, none. Level 1, the facilitator repeats the task wording, which counts as help. Level 2, only after the participant has made no progress for [minutes] minutes or the cap is reached, the facilitator says "Let's move on to the next one" (on the last task of the session, "Let's stop here") and the task is marked Not completed. Any help is written in the notes with the step it was given at.

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
- [Any extra answer a task asks for, written as said:]
- Question it bears on:

Success measures:
- Completed unaided: done condition met with no help.
- Completed with help: done condition met after level 1 help.
- Not completed: done condition not met by the cap.
- Stopped by participant: the participant asks to end the task or the session
  before the done condition is met or the cap is reached. Counted apart from
  Not completed.
- Time on task, wrong turns, ease rating: as recorded in the notes.
- [How an understanding question is counted, if any; marked (default) when the default scale is used.]
- [Task]: counts for [question].
Targets: [as supplied, or "Not set. The product owner sets one for each task before the first session; the plan does not supply them."]

Decisions to settle before recruiting:
D1. Recording (none, audio, screen and audio, or video and screen): [status]. Owner: research lead.
D2. Consent wording: [status]. This plan does not write or judge it.
D3. Who may see notes and recordings, and how long they are kept: [status]. Owner: research lead.
D4. Test data: [status].
D5. Names in notes: participant IDs only (default).
The list linking IDs to names is kept apart by the research lead.
D6. Incentive for participants: [status]. Owner: product owner.
D7. Language and access needs: [status]. Owner: research lead.

Coverage:
Questions: [label, tasks; "in part" and why, where a task answers only part of a question].
Pain points: [label, tasks].
Screens: [label, tasks].
No task: [labels, or "None."]
Conflicts between inputs: [labels, or "None."]

Open questions: [n].
O1. [Question.] Owner: [role].

Approvals (left empty):
Research lead approves method and recruitment: ____________
Product owner confirms what is tested: ____________

Every line traces to the inputs supplied, except the items marked (default).
This plan holds no participant findings.
It recruits nobody, contacts nobody and judges no design.
```

## Before relying on it

Decide every item under "What to customize" in TEMPLATE.md and set the limits the instructions in this file leave open, written in square brackets such as [N], to your own. Then run the acceptance tests in TEMPLATE.md on past work. A person starts this work, supplies the inputs and decides what happens with the result.

# Implementation blocker brief: trial on its invented example

- **Product:** Claude, run in Claude Code
- **Model:** Claude Sonnet 5.5 (model ID claude-sonnet-5-5)
- **Date:** 2026-11-10

Two runs are recorded. The first run was made on the template as first written, and its record is kept below word for word. The template, the example and this record were then revised after the first run's findings (compared below), and the second run was made on the revised template. The inputs are the invented example in `public/example.md`. No client data was used.

## Second run, on the revised template

**How it was run, plainly.** This was not an isolated session. The same session that revised the template made the second run, with file access, and it had already read the example output from the first version. The inputs were taken from `public/example.md` and the revised instruction block and output format in `member/template.md` were applied to them step by step; the example output was then rewritten to match. Because of that, agreement between this run and the example shows only that the revised rules give one reading, not that a fresh reader would reach it. A run with no tools and no access to any file has not been made on the revised template.

**Later clarifications, not re-run.** After this run, the fenced instruction block was clarified to match the procedure (the type mapping, two more gap types, the exclusion of slipped milestones from the downstream list, and the wording on dates). The output format and the example inputs did not change, and the run was not repeated.

**What the run produced.** Every section, in order, with no stop. Late: M2 18 days, M3 11, M4 4; M5 7 days and M6 14 days from today. Six blockers in the same order as before (B1 R3, B2 R1, B3 change window, B4 R4, B5 R5, B6 R6). Waiting on: B1 our side; B2 to B6 the customer, because the revised rule reads a customer's own constraint or hold-back ("can change only in a monthly window", "held back until the field mapping is agreed", "has not been looked at yet", "will name ... next week") as the customer. Summary: 6 blockers, 5 on the customer, 1 on our side, 0 not stated; missing an owner: B3, B6. Gaps: five, three of them customer statements with no date (security team "no date", reviewers "next week", "December quarter-end"). Dates in the record: 2026-10-26 and 2026-12-05 only. Points: one line under "Our side first" (B1), then five numbered questions, one each for B2, B3, B4, B5 and B6, each ending "Concerns" and one blocker id. The closing status line was printed as specified.

**What was checked.** Waiting-on values are all one of the three allowed words. Each point concerns one blocker and no point is about a milestone or the quarter-end. No point asks about a route round a blocker. Days late and days ago were recomputed from today (2026-11-17): 18, 11, 4; 7 and 14 ahead; 14, 12, 5 days ago. Nothing was sent, no access was confirmed and no date was computed or offered (the four days in gap 2 are a count between two stated dates). The fenced instruction block was read line by line against the procedure and the output format.

**Where the revised template still leaves a judgement.**

1. Whether the 2026-11-12 window line also bears on the administrator account (B2) is not decided by the words, so the template now sends that doubt to the gaps (gap 2) and the line is quoted under B3 only.
2. Linking B3 to M2 rests on the words "single sign-on" in the record, which the revised rule allows and requires the brief to show. A stricter reader could still find the match too loose.
3. Reading "reviewing" and "will name or send" as the customer's move is a rule of the template, not a fact in the inputs; a team that wants those marked "not stated" should change it under customization.

**Shortcomings of the second run.** One run, one model, not isolated, on one invented example. It does not show how the template behaves on messy real exports, on the stop conditions, or in other AI products. The acceptance tests in the template were not run.

## First run, 2026-11-10, on the template as first written (kept as recorded)

The inputs for this trial are the invented example in `public/example.md` (settings, implementation plan, readiness checklist, integration notes and meeting records for the invented Customer B). No client data was used. The assistant followed the instruction block and output format in `member/template.md` on those inputs without reading the published example output first, and the two were compared afterwards. The run was one pass by one person's session; it was not repeated.

### Inputs used

The five inputs in the "The inputs" section of `public/example.md`, in full: settings (today is 2026-11-17), the six-row plan, the six-row checklist, three lines of integration notes and two meeting records.

### What came out

The assistant produced every section of the format, in order. Substantial parts:

- **Late milestones:** M2 18 days, M3 11 days, M4 4 days. M5 (7 days away) and M6 (14 days away) listed as at risk downstream.
- **Six blockers, ranked:** B1 firewall allow-list (R3), B2 administrator account (R1), B3 identity-settings change window (not on checklist), B4 sample extract (R4), B5 field mapping sign-off (R5), B6 named reviewers (R6).
- **Waiting on:** B1 our side; B2, B5, B6 the customer; B3 and B4 "not stated".
- **Summary line:** 6 blockers, 3 waiting on the customer, 1 on our side, 2 not stated. Two blockers missing an owner on either side (B3, B6).
- **Gaps:** the B3 window (2026-12-05) falls after the planned go-live (2026-12-01); the record does not say whether the administrator account also waits for the window; "December quarter-end" gives no date; R3 has no update date and no record that the question was asked.
- **Dates in the record:** the mapping sheet sent 2026-10-26, the security team "no date", "December quarter-end", "next week" and the 2026-12-05 window, each with its source.
- **Points for the conversation:** one line under "Our side first" (B1), then five questions: IT admin on B2, IT admin and Operations director on B3, Data owner on B4, Data owner on B5, Operations director on B6.
- **Closing status line:** printed as specified.

### What was observed

Every required part was produced and nothing triggered a stop. No header or status word failed to match, a milestone was slipped, and the inputs held no password or key. Nothing was sent, no access was confirmed as working and no date was computed or offered.

Where the template was ambiguous and the assistant had to judge:

1. **Whose move a record describes.** Step 9 says "waiting on" comes only from the words of the latest record. For the change window ("can change only in a monthly window") and for the 120 held-back sample records ("held back until the field mapping is agreed") the words do not say whose move it is, so both were marked "not stated". Another reader could reasonably say the customer.
2. **Which record concerns which blocker.** The 2026-11-12 line about the monthly window mentions the single sign-on app registration, which also depends on the administrator account (B2). The assistant gave it to the change window (B3) and kept 2026-11-05 as B2's latest record. The template does not say what to do when one line concerns two blockers.
3. **Linking a notes-only blocker to a milestone.** Step 7 needs a milestone named by the record. The window record names the "single sign-on app registration", not M2. Linking it to M2 ("Single sign-on connected") is an inference, which step 5 says not to make.
4. **Type for a checklist row that is also a dependency.** R4 is a data item by category but also waits on R5. Step 6 says to take the type from the category, so it is a data question, with the dependency shown under "Depends on".
5. **Named third parties.** The customer's security team is named in the notes. The assistant treated it as part of R1 rather than as a separate blocker; step 5 could be read either way.
6. **"One numbered point per blocker."** Step 15 asks for one point per blocker waiting on the customer or not stated. With five such blockers the assistant wrote five points. Combining related blockers into one question would read better in a real call, but would break the rule.
7. **Summary format.** The line "Blockers missing an owner" does not say whether to give blocker numbers or checklist item ids. Blocker numbers were used.
8. **Fenced block versus procedure.** The fenced instruction block is shorter than the procedure. It leaves out, among others, the "days late: not applicable" case, what to do with a checklist row that has a blank `needed_for`, and the rule on a missing checklist. A reader who only pastes the fenced block loses those.
9. **Dates in the record.** The template does not say whether the plan's own planned dates belong in this section. The assistant listed only dates and phrases stated in notes and meetings.

### Comparison with the published example (the example as first written)

The slipped milestones, days late, downstream milestones, blocker order (B1 R3, B2 R1, B3 window, B4 R4, B5 R5, B6 R6), statuses, owners, latest records and days ago all matched. Differences:

1. **Waiting on.** The example marks the change window and the sample extract as waiting on the customer; the trial marked them "not stated". So the summary differs: the example has 5 on the customer, 1 on our side, 0 not stated; the trial has 3, 1 and 2. The example also writes "customer (their change window)", a value outside the three allowed words.
2. **Points.** The example has five points, but two are about B2 and none is about B4 alone; its fifth point concerns "B3, M6", a milestone id the format does not call for, and asks about the December quarter-end, which is not a blocker. The trial has one point per blocker. The example's "Our side first" line tells the lead to decide who asks; the trial's line states what waits on our side.
3. **Dates in the record.** The example lists the plan's planned dates; the trial lists the 2026-10-26 mapping sheet date and the security team's "no date" instead.
4. **Gaps.** The example has three gaps, including the window falling four days after go-live. The trial has the same finding without computing the four days (a count of days, not a new date) and adds the missing record for R3 and the unclear B2 and window link.

Facts not in the inputs: none were found in the trial output. In the example output, the question "whether the customer has any route to an earlier change" in point 2 goes beyond the record, though it is phrased as a question and offers no date.

### Shortcomings of the first run

One run, one model, one invented example. It does not show how the template behaves on messy real exports, on the stop conditions, or in other AI products. The acceptance tests in the template were not run.

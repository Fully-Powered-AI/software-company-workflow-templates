# Buyer security questionnaire answers: one trial on the invented example

- **Product:** Claude, run in Claude Code
- **Model:** Claude Sonnet 5.5 (model ID claude-sonnet-5-5)
- **Date:** 2026-11-10

This was one run of the workflow template on its own invented example. The inputs are the invented ones in [the example](example.md): Larchfield Software, Buyer X, eight questions and nine evidence entries. No client data was used. The model that ran it did not write the template. It read the template and the example's inputs first, followed the instruction block and output format, and only then compared the result with the example's published output.

## Inputs used

The inputs listed under "What the person supplies" in `public/example.md`: the company and the run (as-of date 10 November 2026), the rules for the response, the eight questions Q1 to Q8, and the evidence register E1 to E9.

## What came out

```
BUYER SECURITY QUESTIONNAIRE ANSWERS: Buyer X, 8 questions

For: Alicia Ward (sales owner). Verified by: Dana Kessler (security owner). Questionnaire received 2 November 2026. As of 10 November 2026.

Freshness limits used: policies, test records and certificates not older than 10 November 2025; configuration exports not older than 12 August 2026.

Q1: Is customer data encrypted at rest?
  Mark: Partial
  Draft answer: Production database and file storage volumes are encrypted at rest with AES-256.
  Evidence: E1, configuration export, 2026-10-06, 35 days old, in date.
  Limits: backups are not covered by this export. The question asks about customer data, and backups hold customer data.
  Reviewer: Tomas Rehn.

Q2: Is multi-factor authentication required for staff access to production systems?
  Mark: Stale
  Draft answer: Not drafted. The enforcement evidence is past its limit. Closest evidence for the reviewer: E2 ("Multi-factor authentication is required for all staff accounts.") and E3 ("The identity provider enforces multi-factor authentication for the staff group.").
  Evidence: E3, configuration export, 2026-06-20, 143 days old, over the 90-day limit. E2, policy, 2026-02-14, 269 days old, in date.
  Limits: E2 states the requirement only. E3 is the evidence that it is enforced and it is out of date. The register does not say whether the staff group covers access to production systems.
  Reviewer: Dana Kessler.

Q3: Is an independent penetration test carried out each year on all customer-facing components? Please attach the latest report.
  Mark: Partial
  Draft answer: An independent penetration test of the web application and the API was completed in March 2026.
  Evidence: E4, test record (summary), 2026-03-09, 246 days old, in date.
  Limits: the mobile app and internal network were out of scope. The register shows one test, not an annual cycle. E4 is a summary, not the report the buyer asks for.
  Reviewer: Dana Kessler.

Q4: Do you have a documented incident response plan that has been exercised in the last 12 months?
  Mark: Stale
  Draft answer: Not drafted. The plan's source date is past the limit and no exercise is recorded. Closest evidence for the reviewer: E5 ("A documented incident response plan is maintained.").
  Evidence: E5, policy (incident response plan v2), 2025-08-21, 446 days old, over the 12-month limit.
  Limits: no record of an exercise.
  Reviewer: Dana Kessler.

Q5: Do you hold SOC 2 Type II or ISO 27001 certification?
  Mark: Unverifiable
  Draft answer: Not drafted. No entry in the register concerns a certification.
  Evidence: none.
  Limits: nothing can be said about certification unless the security owner supplies a certificate or report.
  Reviewer: Dana Kessler.

Q6: How often is customer data backed up, and how long are backups kept?
  Mark: Supported
  Draft answer: Customer data is backed up daily and backups are kept for 35 days.
  Evidence: E6, configuration export, 2026-09-30, 41 days old, in date.
  Limits: restore testing is not covered.
  Reviewer: Tomas Rehn.

Q7: Do you assess subprocessors before use? Please list them.
  Mark: Partial
  Draft answer: Subprocessors are assessed before use. (The list is not drafted.)
  Evidence: E7, policy (vendor management policy), 2026-04-02, 222 days old, in date.
  Limits: policy only, with no record that assessments were carried out. No subprocessor list was supplied.
  Reviewer: Dana Kessler.

Q8: In which regions is customer data stored?
  Mark: Unverifiable
  Draft answer: Not drafted. Two entries disagree and the assistant does not choose between them.
  Evidence: E8, configuration export, 2026-10-20, 21 days old, in date: "Production customer data is stored in Region North only." E9, policy, 2026-01-15, 299 days old, in date: "Customer data may be stored in Region North and Region South."
  Limits: the entries conflict.
  Reviewer: Tomas Rehn (hosting).

Counts: Supported 1 (Q6). Partial 3 (Q1, Q3, Q7). Stale 2 (Q2, Q4). Unverifiable 2 (Q5, Q8). Total 8 of 8 questions.

Disclosure decisions needed: Q3, the latest penetration test report is requested; Dana Kessler decides whether it is shared and on what terms. Q7, a list of subprocessors is requested; Dana Kessler decides whether it is shared and on what terms.

Held for the security owner: 7. 1. Tomas Rehn: is customer data in backups encrypted at rest, and can a configuration export show it for Q1? 2. Dana Kessler: can a current configuration export for the identity provider be supplied for Q2, and does the staff group cover production systems? 3. Dana Kessler: can the latest penetration test report be shared for Q3, and is there evidence of a yearly cycle and of the mobile app being tested? 4. Dana Kessler: is there a current incident response plan and a record of an exercise in the last 12 months for Q4? 5. Dana Kessler: is there a SOC 2 Type II or ISO 27001 certificate or report for Q5? 6. Dana Kessler: can a subprocessor list and assessment records be supplied for Q7? 7. Tomas Rehn and Dana Kessler: which of E8 and E9 is correct for Q8?

Every answer traces to the evidence register as supplied. This matrix assesses no control, claims no compliance and sends nothing. Alicia Ward sends only the response Dana Kessler has approved.
```

## What was observed

- Every required part was produced: all eight blocks in the buyer's order, the freshness line, the counts (they add up to 8 of 8), disclosure decisions, held questions and the closing line. Nothing in the run reached a stop condition: headers matched, the register was present and every entry had a date.
- Every draft answer is word for word an approved statement from the register. Every fact in the output (names, dates, ages, versions) comes from the inputs.
- Ages and cutoffs were computed by counting days by hand. They agree with the published example for every entry.

Differences from the published example:

- **Q1.** This run marked it Partial; the example marks it Supported. The register says backups are not covered, and the template says a limit the register states makes an answer Partial. The example lists the same limit but marks it Supported. The run's reading follows the written rule, so either the example or the rule is wrong.
- **Q7 disclosure.** This run lists the subprocessor list as a disclosure decision, because the procedure says any request for a list goes there. The example lists only the Q3 report.
- **Held questions.** This run holds seven (the example holds six), because Q1 is Partial here and the procedure holds every partial answer. This run also folded the Q3 report-sharing question into the Q3 held question.
- **Counts.** This run: Supported 1, Partial 3. The example: Supported 2, Partial 2. The other counts match.
- **Freshness line.** This run added certificates to the first limit, as the template's output format does. The example leaves them out.
- **Wording.** Minor differences: this run shows "in date" on every evidence line, as the format asks, and quotes E2 and E3 beside the Not drafted answer for Q2.

Where the instructions were ambiguous and a guess was needed:

- Whether a stated limit that touches the question makes an answer Partial or still Supported (Q1). The rule says Partial for "a limit the register states" and Supported when "no stated limit contradicts it", which can be read both ways.
- Stale against Unverifiable for Q4. A plan exists but is out of date, and nothing shows an exercise. The run followed "first mark that applies" and chose Stale.
- Stale against Partial for Q2. A policy in date and a stale enforcement export both exist. The run chose Stale because the export is the evidence the practice is in place.
- Whether a Not drafted answer may quote the closest evidence. The procedure asks for it for the reviewer, but the format shows only the reason. This run put it in the Draft answer line.
- Whether the mobile app counts as a "customer-facing component" in Q3. The run could not tell and left it as a gap for the security owner.
- The "Held for the security owner" line. The format reads "[n]. [Number. Named person: question.]", and the example's "Held ... : 1. Dana Kessler: ..." reads as a count of one. This run printed the count first, then numbered the questions.
- Whether a held question needs its own line when the question is also a disclosure decision (Q3).

Shortcomings:

- The template states the mark rules in two places, the procedure and the instruction block, and they are worded a little differently. The instruction block leaves out the "no source date" rule and the rule for questions the register cannot show.
- The acceptance tests are marked as proposed and none was run as part of this trial. This trial covered one example only.
- This is one run by one model on an invented example. It says nothing about how the template performs on a real register, and no client environment was involved.

Changed after the run recorded above, and not run again. The output and observations above are as recorded and describe the template and example as they stood at the run:

- **Mark rules.** A stated limit that leaves part of what the question asks uncovered gives Partial (Q1, backups hold customer data); a limit about something the question does not ask (Q6, restore testing) stays Supported. Stale outranks Unverifiable and Partial, which settles Q4 and Q2 as the run guessed them.
- **The example.** Q1 is now Partial with a held question for Tomas Rehn, Q7's list is among the disclosure decisions, the counts are Supported 1 (Q6) and Partial 3 (Q1, Q3, Q7) with 7 held, "in date" is on every evidence line, certificates are in the freshness line, and the held count is printed first. The example now matches this run's output apart from small wording.
- **Where the closest evidence goes.** The output format now says a Not drafted answer carries it in the Draft answer line, as the run did.
- **The pasted instructions** now carry the rules that were only in the procedure: no source date is stale, an unshowable question is Unverifiable and held, the recent-period test for Stale, and the closest evidence in a Not drafted answer.
- **The profile** now mentions this recorded run.

Changed again after the run, after an independent review, and not run again. The recorded output and observations above are unaltered:

- **Q7 wording.** The recorded run, like the example at the time, added "(The list is not drafted.)" to the Q7 draft answer. That is not approved wording, so the observation above that every draft answer is word for word an approved statement did not hold for Q7. The example now carries the draft answer as the approved statement only and puts the remark in Limits.
- **Q8 reviewers.** The example now names both Tomas Rehn and Dana Kessler for Q8, as the held question does; the recorded run named Tomas Rehn.
- **Rules line.** The example's rules now name certificates beside policies and test records; the recorded run's freshness line already did.
- **Conflicts.** The mark rules now say a conflict between entries is Unverifiable even when one entry is past its cutoff, and that Stale outranks Partial. The earlier note above that Stale outranks Unverifiable no longer applies; Q2 and Q4 are unaffected, since neither has conflicting entries.
- **Quoted wording.** The run's notes above refer to wording that no longer exists ("no stated limit contradicts it" and the earlier Held line); they describe the template and example as they stood at the run.
- **The profile** now describes the finance and healthcare buyers as buyers of a software supplier's services.

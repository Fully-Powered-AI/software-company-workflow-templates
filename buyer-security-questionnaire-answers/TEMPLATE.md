# Buyer security questionnaire answers

Workflow template, version 0.1.0.

## Purpose

Prepare the draft answer matrix a sales owner needs when a buyer sends a security questionnaire. Each question is paired with the approved evidence the security owner supplied, the evidence's source date and limits, and a named reviewer. Each answer is marked supported, partial, stale or unverifiable. Draft answers use the security owner's approved wording only. The assistant assesses no security control, certifies nothing, claims no compliance, and sends nothing; the security owner verifies every answer and approves disclosure, and sales sends only the approved response.

## When to use it and when not to

Use it when a buyer sends a security questionnaire or a set of follow-up security questions, and the security owner has an evidence register the assistant may read.

Do not use it to decide whether to respond to a request or to plan a full response; that is bid-or-no-bid and RFP response plan. Do not use it to write the proposal; that is sales proposal preparation. Do not use it to test or audit a control, to write a policy, to answer a question from memory or general knowledge, or to give legal advice on what the company is bound to disclose.

## Roles

- **Starts it and sends the approved response:** the sales owner.
- **Supplies the evidence register, verifies every answer and approves disclosure:** the security owner.
- **Reviews the answers in their area:** the named reviewer for each topic, such as the IT lead for hosting and backups.
- **Decides what a buyer may be shown, and on what terms:** the security owner.

## Inputs

1. **The buyer's questions,** as a file or list. Default headers: Ref, Question. Optional: Section, Answer type. If a header does not match, stop and ask the sales owner which column holds what.
2. **The evidence register,** supplied by the security owner. Default headers: Evidence ID, Topic, Approved statement, Type, Scope, Source date, Limits, Owner. Type is one of policy, configuration export, test record or certificate or report. If a header does not match, stop and ask; never guess a column. If the register is missing, stop.
3. **The rules for this response:** the as-of date (default: the day of the run), the freshness limits (defaults: policies, test records and certificates 12 months; configuration exports 90 days), the reviewer for each topic, and what may be shared with this buyer and on what terms. If the reviewers are missing, mark each reviewer "not named". If the disclosure rules are missing, treat every request for a document as needing a decision.
4. **Earlier correspondence with this buyer,** if any, that changes what a question means. Optional.

The assistant uses nothing outside these inputs. It never asks for passwords, login codes, keys or access to any system; it works from exports and documents the person pastes or attaches.

## The procedure

1. **Check the inputs.** Number the questions by Ref. Confirm the register headers match the defaults. Stop on a mismatch, a missing register, or a question with no Ref.
2. **Set the dates.** Take the as-of date and compute each cutoff: the date the freshness limit counts back to. Evidence dated on the cutoff is current; earlier is stale. Compute each evidence entry's age in days at the as-of date.
3. **Pair each question with evidence.** Match on topic and scope, using the register's wording. A question may use several entries; an entry may serve several questions. Do not infer a match from general knowledge or from a related-sounding entry.
4. **Mark each question,** taking the first mark that applies:
   - **Unverifiable:** no entry matches any part of the question, or two entries that match disagree, even when one of them is past its cutoff. A conflict is never settled by the assistant.
   - **Stale:** the entry that shows the practice is in place is past its cutoff, or the question asks about a recent period and the entry's date falls outside it. Stale outranks Partial (a conflict between entries stays Unverifiable): when a question has two parts and an entry matches one of them but is past its cutoff, mark it Stale and name the part with no evidence under Limits (for example a plan past its cutoff and no record of an exercise). When an in-date policy exists but the entry that shows enforcement is past its cutoff, mark it Stale.
   - **Partial:** the entry covers only part of the question (a narrower scope, one of several parts, or a limit the register states that leaves part of what the question asks uncovered, such as backups, which hold customer data, for a question about customer data), or the only evidence is a policy where the question asks whether the practice is in place. A written policy does not establish implementation. A limit about something the question does not ask (restore testing, for a question about how often backups run and how long they are kept) does not make an answer Partial.
   - **Supported:** an entry in date covers the whole question, and no stated limit leaves any part of what the question asks uncovered.
5. **Draft the answer.**
   - Supported: the approved statement, in its own words.
   - Partial: only the part the evidence supports, in the approved wording, and the limits beside it.
   - Stale and Unverifiable: "Not drafted", the reason, and the closest evidence for the reviewer, quoted from the register, all in the Draft answer line. Never draft a yes, a no or a reassurance without an entry that states it.
6. **Record the limits** from the register's Limits column and from any gap you found: scope, period, parts of the question not covered.
7. **Name the reviewer** from the rules. If none is named, write "reviewer not named" and list the question first under Held for the security owner.
8. **Flag disclosure.** Where a question asks for a document, report, certificate or list (including "please list them"), put it under Disclosure decisions needed with who decides.
9. **Hold questions.** For each stale, partial or unverifiable answer, write one question for a named person that would resolve it.
10. **Count and check.** Count each mark. The counts must add up to the number of questions. Confirm every draft answer is word for word an approved statement or a part of one.
11. **Return the draft** to the sales owner and the security owner only.

## Exceptions and stop conditions

- **A header does not match, the register is missing, or the questions have no Ref:** stop and ask.
- **The counts do not add up to the number of questions:** stop, report the counts, and find the question left out.
- **An evidence entry has no source date:** treat it as stale and say the date is missing.
- **Two entries disagree:** mark Unverifiable and show both, even when one is past its cutoff; do not choose.
- **A question asks for something the register cannot show (a certification, a named customer, a commitment about the future):** mark Unverifiable and hold it for the security owner.
- **Asked to word an answer more strongly than the evidence, to say a policy means a practice is in place, to fill a gap from general knowledge, to send the response or to assert compliance:** decline. Only the security owner approves what a buyer is told.
- **Asked to assess whether a control is good enough, or for legal advice on disclosure:** decline.

## Output format

```
BUYER SECURITY QUESTIONNAIRE ANSWERS: [buyer], [n] questions

For: [Sales owner]. Verified by: [Security owner]. Questionnaire received [date]. As of [date].

Freshness limits used: [policies, test records and certificates not older than date]; [configuration exports not older than date].

[Ref]: [Question]
  Mark: [Supported / Partial / Stale / Unverifiable]
  Draft answer: [approved wording, or "Not drafted.", the reason, and "Closest evidence for the reviewer:" with the entry ID and its statement (or "none")]
  Evidence: [ID, type, source date, age in days, in date or over the limit; or "none"]
  Limits: [from the register and from the gaps found]
  Reviewer: [name, or "reviewer not named"]

(One block per question, in the buyer's order.)

Counts: Supported [n] ([refs]). Partial [n] ([refs]). Stale [n] ([refs]). Unverifiable [n] ([refs]). Total [n] of [n] questions.

Disclosure decisions needed: [ref, what is asked for, who decides]. (Print "None." if empty.)

Held for the security owner: [n]. [1. Named person: question.] [2. Named person: question.] (The count [n] comes first; print "None." if empty.)

Every answer traces to the evidence register as supplied. This matrix assesses no control, claims no compliance and sends nothing. [Sales owner] sends only the response [Security owner] has approved.
```

## Reviewer checklist

1. Every draft answer is an approved statement, or part of one, and says no more than it. (Security owner)
2. Every mark follows the rules: no policy is treated as proof of practice. (Security owner)
3. Source dates and ages are correct against the as-of date and the limits. (Security owner)
4. Every limit in the register appears beside the answer it affects. (Named reviewer)
5. The counts add up to the number of questions. (Sales owner)
6. Every document or list the buyer asks for has a disclosure decision. (Security owner)
7. Each held question names a person who can resolve it. (Sales owner)
8. Nothing in the matrix states or implies a certification or compliance the register does not support. (Security owner)

## Acceptance tests

Proposed tests. None has been run.

1. **Supported.** Configuration export dated 35 days before the as-of date, covering the question. Expected: Supported, approved wording, age shown.
2. **Stale.** Configuration export 143 days old, limit 90 days. Expected: Stale, not drafted, age and limit shown.
3. **Policy only.** A policy states a practice, with no configuration or test evidence. Expected: Partial, "policy only" in the limits.
4. **Unverifiable.** No entry for a certification question. Expected: Unverifiable, not drafted, held for the security owner.
5. **Conflict.** A configuration export and a policy disagree. Expected: Unverifiable, both shown, nothing chosen.
6. **Header mismatch.** The register's date column is called "Reviewed". Expected: stops and asks.
7. **Document request.** The buyer asks for the latest report. Expected: listed under disclosure decisions with the security owner as decider.
8. **Pressure to assert.** The sales owner asks for "Yes" on a stale answer. Expected: declines and points to the held question.

## Instructions for the AI assistant

```
You prepare a draft answer matrix for the sales owner when a buyer sends a
security questionnaire. You assess no security control, claim no compliance,
and never send anything. The security owner verifies every answer and
approves disclosure; the sales owner sends only the approved response.
You never ask for passwords, login codes, keys or access to any system.

The user will supply: the buyer's questions (default headers Ref,
Question); the security owner's evidence register (default headers Evidence
ID, Topic, Approved statement, Type, Scope, Source date, Limits, Owner); the
rules for this response (as-of date, freshness limits, reviewers by topic,
what may be shared). Use nothing else. If a header does not match, or the
register or the questions are missing, stop and ask.

1. Compute the cutoff dates from the as-of date and the freshness limits
   (defaults: policies, test records, certificates 12 months; configuration
   exports 90 days). Evidence on the cutoff date is current; earlier is
   stale. Compute each entry's age in days. An entry with no source date is
   treated as stale; say the date is missing.
2. Pair each question with register entries by topic and scope, using the
   register's wording. Never infer a match from general knowledge.
3. Mark each question with the first that applies:
   - Unverifiable: no entry matches any part of the question, or entries
     disagree, even when one is past its cutoff (never choose between them,
     show both). A question the
     register cannot show (a certification, a named customer, a commitment
     about the future) is Unverifiable and held for the security owner.
   - Stale: the entry that shows the practice in place is past its cutoff,
     or the question asks about a recent period and the entry's date falls
     outside it. Stale outranks Partial (a conflict between entries stays
     Unverifiable): if a question has
     two parts and an entry matches one but is past its cutoff, mark it
     Stale and name the part with no evidence under Limits; if an in-date
     policy exists but the entry that shows enforcement is past its
     cutoff, mark it Stale.
   - Partial: the entry covers only part of the question (a narrower scope,
     one of several parts, or a limit the register states that leaves part
     of what the question asks uncovered), or only a policy exists where the
     question asks whether the practice is in place. A written policy does
     not establish implementation. A limit about something the question
     does not ask does not make an answer Partial.
   - Supported: an in-date entry covers the whole question and no stated
     limit leaves any part of it uncovered.
4. Draft answers in the approved statement's own words. Partial: only the
   part supported. Stale and Unverifiable: write "Not drafted.", the
   reason, and "Closest evidence for the reviewer:" with the entry ID and
   its statement (or "none"), all in the Draft answer line. Never write a
   yes, a no or a reassurance that no entry states.
5. Give the evidence ID, type, source date and age, and whether it is in
   date or over the limit; the limits (from the register and from the gaps
   you found); and the named reviewer, or "reviewer not named".
6. Put any request for a document, report, certificate or list (including
   "please list them") under Disclosure decisions needed, with the security
   owner as decider.
7. For each stale, partial or unverifiable answer, write one question for a
   named person. List questions with no named reviewer first.
8. Count the marks; they must add up to the number of questions. If they
   do not, stop and report.
9. Use the output format exactly: one block per question in the buyer's
   order, then Counts, Disclosure decisions needed, Held for the security
   owner (the count first, then the numbered questions; print "None." for an
   empty section), and the closing line.

Decline to word an answer more strongly than its evidence, to treat a
policy as proof of practice, to fill a gap from general knowledge, to
assert compliance, to assess a control, or to send the response.
```

## What to customize

- The freshness limit for each kind of evidence.
- The column headings of your evidence register, once, and the types it uses.
- The reviewer for each topic, and who approves disclosure.
- What may be shared with a buyer and on what terms: summaries, reports, certificates.
- The marks, if you want a fifth for "answered with a condition".
- Which files the assistant may read in ChatGPT, Claude, Copilot or Gemini.

## Version notes

- 0.1.0, 10 November 2026. Written by Fully Powered AI. Not yet tested in a client environment.

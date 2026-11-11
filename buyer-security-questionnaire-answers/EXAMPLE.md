# Buyer security questionnaire answers: an invented example

*Illustrative example with invented data.* The company, buyer, people, evidence and dates below are made up. They show the inputs a person supplies and the matrix that comes out.

## What the person supplies

**The company and the run.** Larchfield Software, an invented 80-person software company. The sales owner is Alicia Ward. The security owner is Dana Kessler. The IT lead is Tomas Rehn. Buyer X sent an eight-question security questionnaire on 2 November 2026. The assistant is run on 10 November 2026, the as-of date.

**The rules for this response.** Policies, test records and certificates count as current for 12 months (not older than 10 November 2025). Configuration exports count as current for 90 days (not older than 12 August 2026). Reviewers: Tomas Rehn for encryption, backups and hosting; Dana Kessler for everything else. Reports and documents may be shared with a buyer only if Dana Kessler approves, and under a confidentiality agreement.

**The buyer's questions (Ref, Question).**

- Q1: Is customer data encrypted at rest?
- Q2: Is multi-factor authentication required for staff access to production systems?
- Q3: Is an independent penetration test carried out each year on all customer-facing components? Please attach the latest report.
- Q4: Do you have a documented incident response plan that has been exercised in the last 12 months?
- Q5: Do you hold SOC 2 Type II or ISO 27001 certification?
- Q6: How often is customer data backed up, and how long are backups kept?
- Q7: Do you assess subprocessors before use? Please list them.
- Q8: In which regions is customer data stored?

**The evidence register (Evidence ID, Topic, Approved statement, Type, Scope, Source date, Limits, Owner).**

- E1, Encryption, "Production database and file storage volumes are encrypted at rest with AES-256.", configuration export, production database and file storage, 2026-10-06, backups not covered by this export, Tomas Rehn.
- E2, Access control, "Multi-factor authentication is required for all staff accounts.", policy (access control policy v3), all staff accounts, 2026-02-14, states the requirement only, Dana Kessler.
- E3, Access control, "The identity provider enforces multi-factor authentication for the staff group.", configuration export, identity provider, 2026-06-20, none stated, Dana Kessler.
- E4, Testing, "An independent penetration test of the web application and the API was completed in March 2026.", test record (summary), web application and API, 2026-03-09, the mobile app and internal network were out of scope, Dana Kessler.
- E5, Incident response, "A documented incident response plan is maintained.", policy (incident response plan v2), whole company, 2025-08-21, no record of an exercise, Dana Kessler.
- E6, Backups, "Customer data is backed up daily and backups are kept for 35 days.", configuration export, backup service, 2026-09-30, restore testing not covered, Tomas Rehn.
- E7, Vendor management, "Subprocessors are assessed before use.", policy (vendor management policy), all subprocessors, 2026-04-02, no subprocessor list supplied, Dana Kessler.
- E8, Hosting, "Production customer data is stored in Region North only.", configuration export, hosting account, 2026-10-20, none stated, Tomas Rehn.
- E9, Data handling, "Customer data may be stored in Region North and Region South.", policy (data handling policy), whole company, 2026-01-15, none stated, Dana Kessler.

## What comes out

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
  Limits: E2 states the requirement only; E3 is the evidence that it is enforced, and it is out of date. The question says production systems; the register does not say whether the staff group covers them.
  Reviewer: Dana Kessler.

Q3: Is an independent penetration test carried out each year on all customer-facing components? Please attach the latest report.
  Mark: Partial
  Draft answer: An independent penetration test of the web application and the API was completed in March 2026.
  Evidence: E4, test record (summary), 2026-03-09, 246 days old, in date.
  Limits: the mobile app and internal network were out of scope. The register has no evidence of an annual cycle.
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
  Draft answer: Subprocessors are assessed before use.
  Evidence: E7, policy (vendor management policy), 2026-04-02, 222 days old, in date.
  Limits: policy only, with no record that assessments were carried out. No subprocessor list was supplied, so the list is not drafted.
  Reviewer: Dana Kessler.

Q8: In which regions is customer data stored?
  Mark: Unverifiable
  Draft answer: Not drafted. Two entries disagree and the assistant does not choose between them.
  Evidence: E8, configuration export, 2026-10-20, 21 days old, in date: "Production customer data is stored in Region North only." E9, policy, 2026-01-15, 299 days old, in date: "Customer data may be stored in Region North and Region South."
  Limits: the entries conflict; the security owner decides which is right.
  Reviewer: Tomas Rehn and Dana Kessler.

Counts: Supported 1 (Q6). Partial 3 (Q1, Q3, Q7). Stale 2 (Q2, Q4). Unverifiable 2 (Q5, Q8). Total 8 of 8 questions.

Disclosure decisions needed: Q3, the latest penetration test report is requested; Dana Kessler decides whether it is shared and on what terms. Q7, a list of subprocessors is requested; Dana Kessler decides whether it is shared and on what terms.

Held for the security owner: 7. 1. Tomas Rehn: is customer data in backups encrypted at rest, and can a configuration export show it for Q1? 2. Dana Kessler: can a current configuration export for the identity provider be supplied for Q2, and does the staff group cover production systems? 3. Dana Kessler: can the latest penetration test report be shared for Q3, and is there evidence of a yearly cycle and of the mobile app being tested? 4. Dana Kessler: is there a current incident response plan and a record of an exercise in the last 12 months for Q4? 5. Dana Kessler: is there a SOC 2 Type II or ISO 27001 certificate or report for Q5? 6. Dana Kessler: can a subprocessor list and assessment records be supplied for Q7? 7. Tomas Rehn and Dana Kessler: which of E8 and E9 is correct for Q8?

Every answer traces to the evidence register as supplied. This matrix assesses no control, claims no compliance and sends nothing. Alicia Ward sends only the response Dana Kessler has approved.
```

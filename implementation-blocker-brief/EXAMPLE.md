# Implementation blocker brief: an invented example

*Illustrative example with invented data.* The company, the customer, the people, the dates and the records below are all invented. Software Company A is an invented software company; Customer B is an invented customer in its setup phase. First come the inputs the implementation lead supplied, in full, then the brief the capability returned.

## The inputs

### 1. Settings

```
Customer: Customer B
Project: Workflow platform setup
Today: Tuesday 17 November 2026
What counts as a slip: not done, and planned_date before today
```

### 2. Implementation plan (export)

```
milestone_id,milestone,planned_date,status,customer_owner,our_owner,depends_on
M1,Kickoff and project team confirmed,2026-10-12,done,Operations director,Implementation lead,
M2,Single sign-on connected,2026-10-30,in progress,IT admin,Solutions engineer,M1
M3,Sample customer records loaded to the test environment,2026-11-06,in progress,Data owner,Solutions engineer,M2
M4,Workflows configured and reviewed,2026-11-13,not started,Operations director,Implementation consultant,M3
M5,User training,2026-11-24,not started,Operations director,Customer success manager,M4
M6,Go-live,2026-12-01,not started,Operations director,Implementation lead,M5
```

### 3. Readiness checklist (export)

```
item_id,item,category,needed_for,status,customer_owner,our_owner,last_update
R1,Administrator account on the customer's identity provider,access,M2,not received,IT admin,Solutions engineer,2026-10-22
R2,Single sign-on metadata file,access,M2,received,IT admin,Solutions engineer,2026-11-03
R3,Firewall allow-list request for our connection addresses,access,M2,unknown,IT admin,Solutions engineer,
R4,Sample extract of 500 customer records,data,M3,partial,Data owner,Solutions engineer,2026-11-02
R5,Field mapping sign-off,data,M3,not received,Data owner,Implementation consultant,2026-10-28
R6,Named reviewers for the workflow review,people,M4,not received,,Implementation lead,2026-10-15
```

### 4. Integration notes (typed by the solutions engineer)

```
2026-10-20  Single sign-on needs an administrator account on the customer's
            identity provider to create the app registration. The IT admin
            said they would raise it with their security team.
2026-11-03  Metadata file received. We have not yet asked whether the
            customer's firewall needs an allow-list for our connection
            addresses.
2026-11-09  Test load: 380 of the 500 sample records received so far.
```

### 5. Meeting records

```
2026-11-05  Weekly call. Present: Operations director, IT admin,
            Implementation lead. The Operations director said they need to
            be live before the December quarter-end. The IT admin said the
            administrator-account request "is with the security team, no
            date". The Data owner was not on the call.
2026-11-12  Weekly call. Present: Operations director, IT admin, Data owner,
            Implementation lead. The Data owner said the remaining 120
            sample records are held back until the field mapping is agreed,
            and that the mapping sheet we sent on 2026-10-26 "has not been
            looked at yet". The Operations director said they would name the
            workflow reviewers "next week". The IT admin said identity
            settings, including the single sign-on app registration, can
            change only in a monthly window; the next is Saturday
            2026-12-05.
```

## The output

```
IMPLEMENTATION BLOCKER BRIEF: Customer B / Workflow platform setup
Prepared 2026-11-17 from: implementation plan (export), readiness checklist (export), integration notes 2026-10-20 to 2026-11-09, meeting records 2026-11-05 and 2026-11-12. Days counted to 2026-11-17.

SUMMARY
Late: 3 milestones (M2 18 days, M3 11 days, M4 4 days). Blockers: 6 (5 waiting on the customer, 1 on our side, 0 not stated). Blockers missing an owner on either side: 2 (B3, B6).

SLIPPED MILESTONES
M2 Single sign-on connected: planned 2026-10-30, 18 days late, status in progress. Held up by: B1, B2, B3.
M3 Sample customer records loaded to the test environment: planned 2026-11-06, 11 days late, status in progress. Held up by: B4, B5, and M2 (not done).
M4 Workflows configured and reviewed: planned 2026-11-13, 4 days late, status not started. Held up by: B6, and M3 (not done).

AT RISK DOWNSTREAM
M5 User training: planned 2026-11-24, 7 days from today. Waits on M4.
M6 Go-live: planned 2026-12-01, 14 days from today. Waits on M5.

BLOCKERS
B1 Access question: whether the customer's firewall needs an allow-list for our connection addresses (R3)
  Holds up: M2 directly; M3, M4, M5, M6 through the plan's dependencies
  Status: unknown (checklist, no update date)
  Waiting on: our side
  Depends on: none recorded
  Owner, customer side: IT admin. Owner, our side: Solutions engineer.
  Latest record: 2026-11-03, 14 days ago: "We have not yet asked" whether an allow-list is needed.
  Sources: checklist R3; integration notes 2026-11-03

B2 Access question: administrator account on the customer's identity provider (R1)
  Holds up: M2 directly; M3, M4, M5, M6 through the plan's dependencies
  Status: not received
  Waiting on: customer
  Depends on: none recorded
  Owner, customer side: IT admin. Owner, our side: Solutions engineer.
  Latest record: 2026-11-05, 12 days ago: the IT admin said the request "is with the security team, no date".
  Sources: checklist R1 (last_update 2026-10-22); integration notes 2026-10-20; meeting 2026-11-05

B3 Change window: identity settings, including the single sign-on app registration, change only in a monthly window; the next is Saturday 2026-12-05 (not on checklist)
  Holds up: M2 directly (linked by the words "single sign-on" in the record); M3, M4, M5, M6 through the plan's dependencies
  Status: stated in a meeting; not on the checklist
  Waiting on: customer
  Depends on: none recorded
  Owner, customer side: not assigned. Owner, our side: not assigned.
  Latest record: 2026-11-12, 5 days ago: the IT admin named the window.
  Sources: meeting 2026-11-12

B4 Data question: sample extract of 500 customer records (R4)
  Holds up: M3 directly; M4, M5, M6 through the plan's dependencies
  Status: partial; 380 of 500 received (integration notes 2026-11-09)
  Waiting on: customer
  Depends on: B5
  Owner, customer side: Data owner. Owner, our side: Solutions engineer.
  Latest record: 2026-11-12, 5 days ago: the Data owner is holding the remaining 120 records until the field mapping is agreed.
  Sources: checklist R4 (last_update 2026-11-02); integration notes 2026-11-09; meeting 2026-11-12

B5 Data question: field mapping sign-off (R5)
  Holds up: M3 directly; M4, M5, M6 through the plan's dependencies
  Status: not received
  Waiting on: customer
  Depends on: none recorded
  Owner, customer side: Data owner. Owner, our side: Implementation consultant.
  Latest record: 2026-11-12, 5 days ago: the Data owner said the mapping sheet sent 2026-10-26 "has not been looked at yet".
  Sources: checklist R5 (last_update 2026-10-28); meeting 2026-11-12

B6 Missing input: named reviewers for the workflow review (R6)
  Holds up: M4 directly; M5, M6 through the plan's dependencies
  Status: not received
  Waiting on: customer
  Depends on: none recorded
  Owner, customer side: not assigned. Owner, our side: Implementation lead.
  Latest record: 2026-11-12, 5 days ago: the Operations director said they would name the reviewers "next week". No later record.
  Sources: checklist R6 (last_update 2026-10-15); meeting 2026-11-12

WHERE THE SOURCES DISAGREE, AND GAPS
1. B1: the checklist shows R3 as unknown with no update date, and the 2026-11-03 note says our side had not asked. Nothing in the record shows the question was put to the customer since.
2. B3: the planned go-live (M6) is 2026-12-01 and the window in the 2026-11-12 record is 2026-12-05, four days later. The record does not say whether the administrator account (B2) also waits for the window, so the 2026-11-12 line is quoted under B3 only.
3. B2: the IT admin said on 2026-11-05 that the request "is with the security team, no date". The customer statement gives no date.
4. B6: the Operations director said on 2026-11-12 they would name the reviewers "next week". The customer statement gives no date, and nothing is recorded since.
5. M6: the Operations director said on 2026-11-05 that they need to be live before the "December quarter-end". The customer statement gives no date, so the record cannot show whether the planned go-live of 2026-12-01 meets that need. It is not a blocker.

DATES IN THE RECORD
2026-10-26: mapping sheet sent by our side (meeting 2026-11-12)
2026-12-05: next change window for identity settings, a Saturday (meeting 2026-11-12)

POINTS FOR THE CUSTOMER CONVERSATION
Our side first: B1, whether the customer's firewall needs an allow-list for our connection addresses, waits on us; the owner on our side is the Solutions engineer.
1. Raise with the IT admin: who in the security team holds the administrator-account request, and what the customer can tell us about its progress. Concerns B2.
2. Raise with the IT admin: whether the 2026-12-05 window covers the administrator account as well as the single sign-on app registration. Concerns B3.
3. Raise with the Data owner: what the customer needs from us to send the remaining 120 sample records. Concerns B4.
4. Raise with the Data owner: who will review the mapping sheet sent 2026-10-26, and what the customer can tell us about it. Concerns B5.
5. Raise with the Operations director: whether the reviewer names are agreed, and who on the customer's side owns naming them. Concerns B6.

Status: Prepared for the implementation lead. Nothing has been sent to the customer, no integration access has been confirmed and no date has been promised.
```

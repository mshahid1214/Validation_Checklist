# Findings: MediTrack SRS Review

**Reviewers:** Student A and Student B
**Document:** `MediTrack SRS/MediTrack SRS..md` (14 requirements)
**Checklist used:** `Validation Checklist v0.1/Validation Checklist v0.1.md` (20 items)

## 1. Comparing our two runs

We agreed on 17 of 20 answers. Here are the places where we differed or were unsure:

| Item | Student A | Student B | What we agreed |
|------|-----------|-----------|----------------|
| C-07 (two users, same slot) | No ? | Yes ? | **No.** R-03 states a goal ("prevent") but not what the system does in a clash. That is exactly what the clinic is afraid of. |
| C-14 (booking without internet) | No ? | Yes ? | **No.** R-10 only helps people who already came into the clinic. A patient who phones in is not covered. |
| C-17 (cancellation deadline) | No | No ? | **No.** "At any time" means there is no deadline. |
| C-20 (policy reference) | No | ? | **No.** R-13 names no document. B's doubt came from the item wording, so we will tighten it in v0.2. |

**What the disagreements taught us:** C-07 and C-14 weren't easy to answer the same way, so they fail the "Unambiguous" test. In v0.2 we should reword them (see section 4).

## 2. Real problems in the SRS

| # | Req | Problem | Why it matters | Severity |
|---|-----|---------|----------------|----------|
| F-01 | R-04 vs R-05 | **Contradiction.** R-04 says every appointment is 15 minutes. R-05 says doctors choose 10 to 30. | Developers can't build both. The schedule length is core to booking. | High |
| F-02 | R-03 | "Prevent double bookings" has no detail on simultaneous bookings or how a clash is handled. | The manager's biggest worry has no testable rule. | High |
| F-03 | R-09 | "Stored securely" is vague, and no roles are listed for who can see records. | Medical data is private. We can't test "securely". | High |
| F-04 | R-02 | "Respond quickly" has no number or unit. | Can't be tested. Monday mornings are busy, so speed matters most there. | High |
| F-05 | R-10 | Walk-ins can be booked but emergency walk-ins have no priority rule. | Emergencies could wait behind normal bookings. | High |
| F-06 | R-06 | Reminders have no timing (how long before) and no channel (SMS, email, call). | Forgotten appointments cost the clinic money. We can't tell if the requirement is met. | Medium |
| F-07 | R-08 | "User-friendly for all age groups" has no test. | Can't be verified, and elderly patients could be left out. | Medium |
| F-08 | R-01 (+ R-10) | Patients can book **online only**. No way for patients without internet to book remotely. | Elderly patients are excluded. | Medium |
| F-09 | R-12 | "Normal working hours" is undefined, with no uptime number. | Unclear when the system must be up. | Medium |
| F-10 | R-02, R-12 | No expected number of simultaneous users, especially Monday mornings. | The system could be built for the wrong load. | Medium |
| F-11 | R-07 | "Cancel at any time" has no deadline, and nothing says the freed slot is offered to others. | Late cancellations leave empty slots. | Medium |
| F-12 | R-11 | "Active appointment" is not defined, and the document doesn't say what the patient sees at the limit. | Developers will guess. | Low |
| F-13 | R-13 | "Clinic policy" is not named or linked, and payments aren't described anywhere else in the SRS. | Unclear what the system should actually do. May also be out of scope. | Low |
| F-14 | R-07, R-11 | These use "may". The rest use "shall". | Inconsistent wording makes it unclear what is mandatory. | Low |

## 3. What is missing (not covered by any requirement)

- **Clinic administrator:** listed as a user, but no requirement mentions them.
- **Data protection officer:** listed as a user, but no requirement mentions them.
- **Doctor absence or leave:** no rule for what happens to booked patients.
- **Receptionist:** only has R-10 and the cancellation notice in R-07. No rescheduling.
- **Doctor:** R-14 lets them view the schedule only. No way to block time off.

## 4. Fixes for checklist v0.2

- Reword C-07 so two people give the same answer, for example: *"Does the document say how the system decides who gets the slot when two users book at the same moment?"*
- Reword C-14 to name the booking method, for example: *"Does the document describe a way for a patient to book without using the internet?"*
- Reword C-20 as: *"Does R-13 name the document where the clinic policy is written?"* or drop "every reference".
- Add a few items that can be answered **Yes** by a good SRS, so the checklist isn't answered "No" every time. For example, "Does every requirement describe only one function?"
- Add N/A-capable items, such as one for each requirement that mentions a number.

## 5. Quick summary for the clinic

Please **don't sign yet**. The SRS has 14 requirements, and at least 10 of them are too vague to test. Two problems are serious: the contradiction on appointment length, and double booking and medical privacy being described only in general terms. Ask the software company to fix the High items in section 2 before signing.

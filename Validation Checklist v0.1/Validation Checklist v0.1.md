# Validation Checklist v0.1: MediTrack SRS

**Document under review:** `srs/meditrack-srs.md`
**Rule for every item:** answer **Yes**, **No** or **N/A**. **Yes always means the document is fine.**
Every item was checked against the AOUT tests (Atomic, Observable, Unambiguous, Traceable).

The Answer and Evidence columns are left blank on purpose. Each person fills them in on their own run (see `runs/`).

## Where the questions came from

- **Doc rules** = what makes a requirements document good (clear, testable, consistent, complete)
- **Risk** = something that could go wrong at CityCare Clinic
- **User** = what one of the five user roles would look for

## Risks we used

1. Double bookings (manager's #1 worry)
2. Patients forgetting appointments, so the clinic loses money
3. Private medical information leaking
4. Elderly patients who can't use an online system
5. Emergency walk-ins treated like normal bookings
6. Monday-morning overload
7. Late cancellations leaving empty slots
8. A doctor on leave or sick with booked patients

## Checklist

| ID | Item | Answer | Evidence | Where question came from |
|----|------|--------|----------|--------------------------|
| C-01 | Does every requirement have its own unique ID? | | | Doc rules: traceability |
| C-02 | Does every requirement use the word "shall" (not "may")? | | | Doc rules: consistent wording |
| C-03 | Does every speed requirement state a number and a unit? | | | Doc rules: testable. Risk 6 |
| C-04 | Does the document state how many users the system must handle at the same time? | | | Risk 6 (busy Mondays) |
| C-05 | Does the document state availability as a number (for example hours per day or uptime %)? | | | Doc rules: testable |
| C-06 | Are the requirements about appointment length free of contradiction with each other? | | | Doc rules: no contradictions |
| C-07 | Does the document say what happens when two users try to book the same slot at the same moment? | | | Risk 1 (double booking) |
| C-08 | Does the document say how long before an appointment a reminder is sent? | | | Risk 2 (forgotten appointments) |
| C-09 | Does the document say which channel (SMS, email or phone call) is used for reminders? | | | Risk 2. User: Patient |
| C-10 | Does the document say which roles may view a patient's medical record? | | | Risk 3 (privacy) |
| C-11 | Does the document name at least one specific security measure (for example encryption or access logging)? | | | Risk 3. Doc rules: testable |
| C-12 | Is there at least one requirement written for the Data protection officer? | | | User: Data protection officer |
| C-13 | Is there at least one requirement written for the Clinic administrator? | | | User: Clinic administrator |
| C-14 | Does the document describe a way to book for patients with no internet access? | | | Risk 4. User: Patient (elderly) |
| C-15 | Does the document say how an emergency walk-in gets priority over booked patients? | | | Risk 5. User: Receptionist |
| C-16 | Does the document say what happens to booked appointments when a doctor is on leave or absent? | | | Risk 8. User: Doctor |
| C-17 | Does the document state a cancellation deadline (for example hours before the appointment)? | | | Risk 7 (late cancellations) |
| C-18 | Is the term "active appointment" defined in the document? | | | Doc rules: unambiguous |
| C-19 | Does the document give a measurable test for ease of use (for example task completion rate)? | | | Doc rules: testable. Risk 4 |
| C-20 | Does every reference to a policy say where that policy is written? | | | Doc rules: completeness |

## Coverage check

- **5 users covered:** Patient (C-09, C-14, C-19), Doctor (C-16), Receptionist (C-15), Clinic administrator (C-13), Data protection officer (C-12)
- **8 risks covered** (the task asks for at least 5)
- **20 items** (the task allows 15 to 20)
- **Polarity:** "Yes" is the good answer for all 20

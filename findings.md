# MediTrack SRS — Consolidated Findings

## 1. Review basis
The supplied SRS was assessed using the 18-item checklist in `checklist/v0.1.md`. The sample assessments are recorded in `runs/run-A.md` and `runs/run-B.md`.

**Result:** Both sample runs recorded 18 No answers, 0 Yes, and 0 N/A. Findings below consolidate the document gaps. They do not claim that the requirements are impossible to implement.

## 2. Consolidated findings

| Finding | Related requirement(s) | Problem | Risk to CityCare | Recommended clarification |
|---|---|---|---|---|
| F-01: Unmeasurable response time | R-02 | “Respond quickly” has no threshold, unit, or load condition. | Slow booking during busy periods may go unnoticed. | Define a measurable response-time target, including expected Monday-morning workload. |
| F-02: Double-booking behavior underspecified | R-03 | The desired outcome is stated, but conflict detection and simultaneous-request behavior are not. | Two patients may receive the same slot. | Specify atomic slot reservation, conflict rejection, and confirmation behavior. |
| F-03: Appointment duration contradiction | R-04, R-05 | R-04 requires 15 minutes; R-05 allows doctors to select 10–30 minutes. | Developers and testers cannot determine which rule takes priority. | Decide whether 15 minutes is fixed, a default, or one option in the configurable range. |
| F-04: Reminder schedule missing | R-06 | No reminder lead time or delivery channel is specified. | Patients may still forget appointments; reminder behavior cannot be tested. | Define reminder timing, delivery channel, failure handling, and opt-out behavior if applicable. |
| F-05: Cancellation policy unclear | R-07 | “At any time” gives no cutoff or exception. | Late cancellations may disrupt schedules. | Confirm whether cancellation is allowed up to the appointment start and define exceptions. |
| F-06: Accessibility not testable | R-08 | “User-friendly for all age groups” is subjective. | Elderly or less digitally confident patients may be excluded. | Add specific accessibility criteria and testable usability acceptance conditions. |
| F-07: Medical-record privacy controls missing | R-09 | “Stored securely” does not define viewing permissions or access controls. | Unauthorized staff may access confidential information. | Define authentication, role-based authorization, audit logging, and data-protection expectations. |
| F-08: Emergency walk-in handling missing | R-10 | Receptionist walk-in booking is stated, but emergency prioritization is not. | Emergency patients may be treated like routine walk-ins. | Define emergency intake and prioritization, including who can flag an emergency. |
| F-09: Active appointment definition missing | R-11 | The limit of 3 active appointments has no status definition. | Users may be blocked incorrectly or exceed the intended limit. | Define which statuses count as active, including booked, cancelled, completed, and no-show. |
| F-10: Availability is vague | R-12 | “Normal working hours” and an availability target are not defined. | The clinic cannot verify service availability. | Specify operating days/hours, maintenance expectations, and a measurable availability target. |
| F-11: External clinic policy not identified | R-13 | The overdue-payment rule depends on an unspecified policy. | Staff may apply different payment handling. | Attach or reference the approved policy with its version and responsible role. |
| F-12: Administrator responsibilities absent | Stakeholder list; no matching requirement | The administrator is named as a user but no capability or permission is defined. | Administrative work may be unsupported or over-permissioned. | Define administrator tasks and permitted actions. |
| F-13: Doctor schedule boundaries unclear | R-14 | “Daily schedule” does not define the day boundary or time zone. | Schedule views may be inconsistent. | Specify the clinic time zone and start/end boundary of the daily view. |
| F-14: Peak-load requirement absent | Clinic concern; R-02, R-12 | Monday mornings are known to be busy, but no capacity or load requirement is stated. | The system may slow down under peak demand. | Estimate concurrent users and booking volume, then specify performance and capacity targets. |
| F-15: Alternative patient booking route absent | R-01, R-08, R-10 | Online booking is specified, but no assisted route is described. | Elderly or digitally excluded patients may struggle to book. | Confirm whether receptionist/phone-assisted booking is supported for patients who need help. |

## 3. Checklist comparison

| Result | Student A sample run | Student B sample run |
|---|---:|---:|
| Yes | 0 | 0 |
| No | 18 | 18 |
| N/A | 0 | 0 |
| Uncertain (?) | 0 | 0 |

These are sample assessments prepared retrospectively from the same handout. They must not be represented as proof of two actual independent timed reviews.

## 4. Priority before contract approval
1. **Critical:** Resolve the R-04/R-05 duration conflict and specify double-booking prevention.
2. **High:** Define medical-record access controls, emergency walk-in handling, and cancellation behavior.
3. **High:** Make response time, peak-load capacity, and availability measurable.
4. **Medium:** Specify reminder behavior, accessibility criteria, appointment status rules, payment policy, and administrator permissions.
5. **Medium:** Clarify schedule boundaries and alternative booking support.

## 5. Conclusion
The SRS is not sufficiently precise or complete for confident contract sign-off in its current form. It contains a direct appointment-duration conflict and important omissions related to scheduling, privacy, accessibility, peak demand, and operational rules. CityCare should request clarification and measurable acceptance criteria before approving the requirements baseline.

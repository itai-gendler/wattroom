---
appliesTo:
- type: capability
  id: plan-session
- type: capability
  id: move-planned-session
- type: entity
  id: planned-session
references:
- kind: code
  role: implementation
  target: server/internal/crews/schedule.go#plannableAt
- kind: code
  role: implementation
  target: server/internal/crews/crew_schedule.go#handleCrewPlan
---

# A session is planned between now and three months out, and a crew holds at most 100 upcoming plans

Plans may overlap, even in one channel; only a start meets the channel's one-session rule. A plan that started, was cancelled or fell past its grace gives its slot back.

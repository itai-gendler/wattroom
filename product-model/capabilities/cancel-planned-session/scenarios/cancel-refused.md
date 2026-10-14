---
kind: validation
routes:
  web: Web
steps:
- text: The Rider, a plain member, tries to cancel a plan someone else made
  kind: actor
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::crew-schedule
- text: 'The Product refuses: the planner, the owner and admins cancel a plan'
  kind: product
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::crew-schedule
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_schedule.go#mayRearrange
---

# A member cancels someone else's plan

## Trigger

A member tries to call off another member's ride.

## Outcome

The plan stays on the schedule.

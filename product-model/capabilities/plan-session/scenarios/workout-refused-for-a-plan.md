---
kind: validation
routes:
  web: Web
steps:
- text: The Rider plans a workout with a heart-rate hold, or one that runs longer than a day
  kind: actor
  actor: rider
  entities:
  - entity: workout
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-schedule
- text: The Product refuses it and says why in one line
  kind: product
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::crew-schedule
references:
- kind: code
  role: implementation
  target: server/internal/crews/schedule.go#checkPlan
---

# A workout that cannot be a session

## Trigger

A member plans a workout a session cannot ride.

## Outcome

Nothing is planned.

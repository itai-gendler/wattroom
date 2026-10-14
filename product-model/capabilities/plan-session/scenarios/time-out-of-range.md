---
kind: validation
routes:
  web: Web
steps:
- text: The Rider picks a time already past or more than three months out
  kind: actor
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::crew-schedule
- text: The Product refuses and says a session is planned between now and three months out
  kind: product
  actor: rider
  entities:
  - entity: session
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-schedule
references:
- kind: code
  role: implementation
  target: server/internal/crews/schedule.go#plannableAt
---

# A time in the past or too far ahead

## Trigger

A member picks a date far in the future.

## Outcome

Nothing is planned.

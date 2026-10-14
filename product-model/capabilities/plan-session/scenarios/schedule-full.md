---
kind: edge
routes:
  web: Web
steps:
- text: The Rider plans a session
  kind: actor
  actor: rider
  entities:
  - entity: session
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-schedule
- text: The crew already holds 100 upcoming plans
  kind: condition
  entities:
  - entity: planned-session
    effect: reads
    facts:
    - Starts at
  - entity: crew
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-schedule
- text: The Product refuses and says to cancel one, or wait for the next to start
  kind: product
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::crew-schedule
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_schedule.go#handleCrewPlan
---

# A full schedule

## Trigger

A crew has planned months of rides.

## Outcome

Nothing is planned until a slot frees.

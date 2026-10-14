---
kind: primary
routes:
  web: Web
steps:
- text: The Rider chooses Cancel the session on a plan and confirms
  kind: actor
  actor: rider
  entities:
  - entity: planned-session
    effect: reads
    facts:
    - Workout
    - Starts at
  - entity: session
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-schedule
- text: The Product takes the plan off the schedule with its answers and tells the crew
  kind: product
  actor: rider
  entities:
  - entity: planned-session
    effect: removes
    from: Planned
  - entity: answer
    effect: removes
    with: planned-session
  - entity: crew
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-schedule
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_schedule.go
---

# Cancel a plan

## Trigger

Too few riders said they are in.

## Outcome

The plan is gone and the crew knows.

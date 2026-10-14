---
kind: primary
routes:
  web: Web
steps:
- text: The Rider picks a workout, a time and a voice channel under Plan a session
  kind: actor
  actor: rider
  entities:
  - entity: voice-channel
    effect: reads
    facts:
    - Name
  - entity: session
    effect: reads
    facts: []
  - entity: workout
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-schedule
- text: The Product puts the plan on the crew's schedule
  kind: product
  actor: rider
  entities:
  - entity: planned-session
    effect: creates
    to: Planned
    facts:
    - Workout
    - Starts at
    - Voice channel
  - entity: crew
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-schedule
- text: The Product announces it in the voice channel and tells the members who keep Notify me on
  kind: product
  actor: rider
  entities:
  - entity: crew-membership
    effect: reads
    facts:
    - Notify me
  - entity: voice-channel
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-schedule
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_schedule.go#handleCrewPlan
---

# Plan a session

## Trigger

A member wants the crew on the bikes on Tuesday at seven.

## Outcome

The plan is on the schedule with nobody answered yet.

## Edge cases

- Two plans may overlap, even in the same channel; the one-session rule is met when one starts.

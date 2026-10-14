---
kind: alternative
routes:
  web: Web
steps:
- text: The Rider picks a workout and a time and leaves the voice channel open
  kind: actor
  actor: rider
  entities:
  - entity: voice-channel
    effect: reads
    facts: []
  - entity: workout
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-schedule
- text: The Product puts the plan on the schedule naming no voice channel
  kind: product
  actor: rider
  entities:
  - entity: planned-session
    effect: creates
    to: Planned
    facts:
    - Workout
    - Starts at
  - entity: voice-channel
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-schedule
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_schedule.go#enterableChannel
---

# Plan with no channel yet

## Trigger

The crew has not decided which channel to ride in.

## Outcome

The plan asks for a channel when it is started.

---
kind: primary
routes:
  web: Web
steps:
- text: The Rider chooses Start now on a plan that is due
  kind: actor
  actor: rider
  entities:
  - entity: planned-session
    effect: reads
    facts:
    - Workout
    - Starts at
    - Voice channel
  contexts:
    web:
      place: web::signed-in::crew-schedule
- text: The Product opens the session in the plan's voice channel with the Rider as coach and starts its countdown
  kind: product
  actor: rider
  entities:
  - entity: session
    effect: creates
    to: Counting in
    facts:
    - Workout
    - Coach
  - entity: voice-channel
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-schedule
- text: The Product marks the plan started and takes the Rider to the session
  kind: product
  actor: rider
  entities:
  - entity: planned-session
    effect: changes
    from: Planned
    to: Started
    facts: []
  - entity: session
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::session
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_schedule.go#handleCrewStarted
---

# Start now

## Trigger

Ride time comes round.

## Outcome

The session is counting in with the Rider as its coach, and the plan is off the schedule.

## Edge cases

- Start now is offered from 15 minutes before the plan's time; a plan whose time has passed stays startable for 30 minutes.

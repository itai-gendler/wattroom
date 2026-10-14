---
kind: alternative
routes:
  web: Web
steps:
- text: The Rider chooses Start now on a plan with no voice channel and picks one they may enter
  kind: actor
  actor: rider
  entities:
  - entity: voice-channel
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::signed-in::crew-schedule
- text: The Product opens the session there with the Rider as coach
  kind: product
  actor: rider
  entities:
  - entity: session
    effect: creates
    to: Counting in
    facts:
    - Workout
    - Coach
  contexts:
    web:
      place: web::signed-in::crew-schedule
- text: The Product marks the plan started in that channel
  kind: product
  actor: rider
  entities:
  - entity: planned-session
    effect: changes
    from: Planned
    to: Started
    facts:
    - Voice channel
  contexts:
    web:
      place: web::signed-in::crew-schedule
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_schedule.go#handleCrewStarted
---

# Start a plan that named no channel

## Trigger

A plan made before the channel was decided comes due.

## Outcome

The session runs in the chosen channel.

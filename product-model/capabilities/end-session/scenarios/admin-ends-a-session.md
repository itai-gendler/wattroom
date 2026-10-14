---
kind: alternative
routes:
  web: Web
steps:
- text: The Rider, the crew's owner or an admin, ends a session another rider left running
  kind: actor
  actor: rider
  entities:
  - entity: session
    effect: changes
    from: Paused
    to: Ended
    facts: []
  - entity: crew
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::session
- text: The Product saves the rides, awards the medals and frees the channel
  kind: product
  actor: rider
  entities:
  - entity: ride
    effect: creates
    facts:
    - Workout
    - Started at
    - Duration
    - Average power
    - Normalized power
    - Energy
    - Execution score
    - Scored
    - FTP at the ride
    - XP
    - Power curve
    - Samples
    - Ridden with
  - entity: medal
    effect: creates
    facts:
    - Kind
    with: ride
  - entity: session-recap
    effect: creates
    facts:
    - Workout
    - Started at
    - Who was there
  contexts:
    web:
      place: web::signed-in::session
references:
- kind: code
  role: implementation
  target: server/internal/hub/channel_ride.go#refusalLocked
---

# An owner or admin ends someone else's session

## Trigger

A session left paused holds the channel shut.

## Outcome

The channel is free for the next session.

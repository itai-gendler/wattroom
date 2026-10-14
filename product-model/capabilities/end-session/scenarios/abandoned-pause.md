---
kind: edge
routes:
  web: Web
steps:
- text: A session has been paused for 10 minutes with nobody in the channel
  kind: condition
  unattended: true
  entities:
  - entity: session
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::session
- text: The Product ends it and saves its rides
  kind: product
  entities:
  - entity: session
    effect: changes
    from: Paused
    to: Ended
    facts: []
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
  contexts:
    web:
      place: web::signed-in::session
references:
- kind: code
  role: implementation
  target: server/internal/hub/session_end.go#endAbandonedSessionLocked
---

# A paused session nobody is left in

## Trigger

Everyone left a paused session.

## Outcome

The rides are saved instead of waiting for a coach who has gone.

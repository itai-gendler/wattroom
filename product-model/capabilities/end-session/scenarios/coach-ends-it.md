---
kind: alternative
routes:
  web: Web
steps:
- text: The Rider, the session's coach, chooses End
  kind: actor
  actor: rider
  entities:
  - entity: session
    effect: changes
    from: Running
    to: Ended
    facts:
    - Elapsed
  contexts:
    web:
      place: web::signed-in::session
- text: The Product saves each joined rider's ride where the clock stood, awards the medals and keeps the recap
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
  target: server/internal/hub/session.go
---

# The coach ends the session

## Trigger

The crew calls it early.

## Outcome

The session is over and its rides are saved.

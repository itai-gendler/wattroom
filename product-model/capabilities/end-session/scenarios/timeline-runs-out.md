---
kind: primary
routes:
  web: Web
steps:
- text: The shared timeline reaches the end of the workout
  kind: condition
  unattended: true
  entities:
  - entity: session
    effect: reads
    facts:
    - Elapsed
  - entity: workout
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::session
- text: The Product ends the session
  kind: product
  entities:
  - entity: session
    effect: changes
    from: Running
    to: Ended
    facts: []
  contexts:
    web:
      place: web::signed-in::session
- text: The Product saves each joined rider's ride, awards the medals and keeps the session's recap
  kind: product
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
  - entity: rider
    effect: reads
    facts: []
  - entity: session
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::session
- text: The Product pays each rider their ride's XP and any trophy the ride earned
  kind: product
  entities:
  - entity: rider
    effect: changes
    facts:
    - Total XP
    - Level
  - entity: trophy
    effect: creates
    facts:
    - Achievement
    - Earned on
    - XP paid
  - entity: ride
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::session
references:
- kind: code
  role: implementation
  target: server/internal/hub/session_end.go#closeLocked
- kind: code
  role: implementation
  target: server/internal/stats/saver.go
---

# The timeline runs out

## Trigger

The last block of a session ends.

## Outcome

Every rider who rode at least a minute has the ride in their history with its medals, and the crew has a recap.

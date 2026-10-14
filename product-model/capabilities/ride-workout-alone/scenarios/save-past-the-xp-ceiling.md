---
kind: edge
routes:
  web: Web
steps:
- text: The Rider finishes a long ride
  kind: actor
  actor: rider
  entities:
  - entity: ride
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::ride-alone
- text: Rides the browser saved today have already paid close to 6,000 XP
  kind: condition
  entities:
  - entity: ride
    effect: reads
    facts:
    - XP
  contexts:
    web:
      place: web::signed-in::ride-alone
- text: The Product saves the ride with what is left of the day's XP, down to none, and says so
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
  contexts:
    web:
      place: web::signed-in::ride-alone
references:
- kind: doc
  role: intent
  target: docs/spec/stats.md
  title: 'Spec: XP sources'
---

# Past the day's XP ceiling

## Trigger

A rider spends a whole day on the trainer.

## Outcome

The ride is saved; its XP is capped. Session rides are outside the ceiling.

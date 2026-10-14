---
kind: primary
routes:
  web: Web
steps:
- text: The Rider picks a workout and starts it
  kind: actor
  actor: rider
  entities:
  - entity: workout
    effect: reads
    facts:
    - Name
    - Steps
  contexts:
    web:
      place: web::signed-in::ride-alone
- text: The Product counts in for three seconds and drives the trainer at the Rider's own share of FTP for each block
  kind: product
  actor: rider
  entities:
  - entity: rider
    effect: reads
    facts:
    - FTP
  contexts:
    web:
      place: web::signed-in::ride-alone
- text: The Rider pedals to the end, adding a minute or skipping a block when they want
  kind: actor
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::ride-alone
- text: The Product saves the ride, pays its XP and awards any trophy it earned
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
  contexts:
    web:
      place: web::signed-in::ride-alone
- text: The Product shows the ride's summary
  kind: product
  actor: rider
  entities:
  - entity: ride
    effect: reads
    facts:
    - Duration
    - Average power
    - Execution score
    - XP
    - Power curve
  contexts:
    web:
      place: web::signed-in::ride-alone
references:
- kind: code
  role: implementation
  target: server/internal/rides/save.go
- kind: code
  role: implementation
  target: server/internal/gamify/evaluate.go
---

# Ride a workout alone

## Trigger

A rider trains on a night their crew is not riding.

## Outcome

The ride is in their history with its execution score and XP.

## Edge cases

- A ride stopped for 10 minutes ends itself.
- A ride the browser could not save in time is offered back later to save.

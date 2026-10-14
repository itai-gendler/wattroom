---
kind: primary
routes:
  web: Web
steps:
- text: The Rider opens Rides
  kind: actor
  actor: rider
  entities:
  - entity: ride
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::ride-history
- text: The Product lists the Rider's rides, newest first, with the FTP each was scored against and the power curve
  kind: product
  actor: rider
  entities:
  - entity: ride
    effect: reads
    facts:
    - Workout
    - Started at
    - Duration
    - Average power
    - XP
    - FTP at the ride
    - FTP produced
    - Ridden with
  contexts:
    web:
      place: web::signed-in::ride-history
references:
- kind: code
  role: implementation
  target: server/internal/rides/rides.go
---

# Read your history

## Trigger

A rider checks their progress.

## Outcome

The rider reads their rides and their FTP over time.

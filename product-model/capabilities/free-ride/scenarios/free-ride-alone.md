---
kind: primary
routes:
  web: Web
steps:
- text: The Rider chooses Free ride, opening at 0 % grade, and pedals
  kind: actor
  actor: rider
  entities:
  - entity: ride
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::ride-alone
- text: The Rider ends the ride
  kind: actor
  actor: rider
  entities:
  - entity: ride
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::ride-alone
- text: The Product saves it as an unscored Free ride and pays its XP
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
    - Energy
    - Scored
    - XP
    - Samples
  - entity: rider
    effect: changes
    facts:
    - Total XP
    - Level
  contexts:
    web:
      place: web::signed-in::ride-alone
references:
- kind: code
  role: implementation
  target: server/internal/rides/save.go
---

# Free ride alone

## Trigger

A rider wants to spin with no plan.

## Outcome

The free ride is in their history.

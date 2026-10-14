---
kind: primary
routes:
  web: Web
steps:
- text: The Rider opens a ride from their history
  kind: actor
  actor: rider
  entities:
  - entity: ride
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::ride-page
- text: The Product shows its numbers, trace, medals and the crew and channel it was ridden in
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
    - Normalized power
    - Energy
    - Execution score
    - Scored
    - FTP at the ride
    - XP
    - Power curve
    - Samples
    - Ridden with
    - RPE
    - Note
  - entity: medal
    effect: reads
    facts:
    - Kind
  - entity: crew
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::ride-page
references:
- kind: code
  role: implementation
  target: server/internal/rides/detail.go
---

# Open a ride

## Trigger

A rider looks back at last Tuesday's session.

## Outcome

The rider reads everything the ride recorded.

## Edge cases

- A crew the rider has since left, or that banned them, is named and not linked.

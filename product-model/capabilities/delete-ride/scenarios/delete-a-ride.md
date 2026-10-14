---
kind: primary
routes:
  web: Web
steps:
- text: The Rider deletes a ride and confirms
  kind: actor
  actor: rider
  entities:
  - entity: ride
    effect: removes
  - entity: medal
    effect: removes
    with: ride
  contexts:
    web:
      place: web::signed-in::ride-page
- text: The Product keeps the Rider's total XP where it was
  kind: product
  actor: rider
  entities:
  - entity: rider
    effect: reads
    facts:
    - Total XP
  contexts:
    web:
      place: web::signed-in::ride-page
references:
- kind: code
  role: implementation
  target: server/internal/rides/rides.go#handleDelete
---

# Delete a ride

## Trigger

A rider does not want a ride kept.

## Outcome

The ride and its samples are gone; the rider's level does not move.

---
kind: edge
routes:
  web: Web
steps:
- text: The Rider ends a free ride before a minute of pedalling
  kind: actor
  actor: rider
  entities:
  - entity: ride
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::ride-alone
- text: 'The Product saves nothing: a ride under a minute is not saved'
  kind: product
  actor: rider
  entities:
  - entity: ride
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::ride-alone
references:
- kind: code
  role: implementation
  target: server/internal/rides/save.go
---

# Under a minute

## Trigger

A rider tests the trainer and stops.

## Outcome

No ride is saved.

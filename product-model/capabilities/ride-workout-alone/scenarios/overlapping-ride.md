---
kind: validation
routes:
  web: Web
steps:
- text: The Rider's browser saves a ride sharing a second with a ride already on the account
  kind: actor
  actor: rider
  entities:
  - entity: ride
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::ride-alone
- text: 'The Product refuses it: nobody rides two at once'
  kind: product
  actor: rider
  entities:
  - entity: ride
    effect: reads
    facts:
    - Started at
    - Duration
  contexts:
    web:
      place: web::signed-in::ride-alone
references:
- kind: code
  role: implementation
  target: server/internal/rides/save.go
---

# A ride at a time already taken

## Trigger

A ride is uploaded twice, or from two devices.

## Outcome

Only the first is kept.

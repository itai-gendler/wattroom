---
kind: primary
routes:
  web: Web
steps:
- text: The Rider chooses Leave the ride
  kind: actor
  actor: rider
  entities:
  - entity: ride
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::session
- text: The Product takes the Rider out of the ride; what they rode is saved when the session closes
  kind: product
  actor: rider
  entities:
  - entity: session
    effect: changes
    facts:
    - Riders in the ride
  - entity: ride
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::session
references:
- kind: code
  role: implementation
  target: server/internal/hub/channel_ride.go
---

# Leave the ride

## Trigger

A rider's legs are done before the session is.

## Outcome

The rider is no longer in the ride and stays in the channel.

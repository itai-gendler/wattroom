---
kind: validation
routes:
  web: Web
steps:
- text: The Rider hands the session to someone who has not joined the ride
  kind: actor
  actor: rider
  entities:
  - entity: session
    effect: reads
    facts: []
  - entity: ride
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::session
- text: The Product refuses and asks for someone riding in it
  kind: product
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::session
references:
- kind: code
  role: implementation
  target: server/internal/hub/channel_ride.go#handOffLocked
---

# Handing to someone not in the ride

## Trigger

The coach picks a listener.

## Outcome

The coach keeps the session.

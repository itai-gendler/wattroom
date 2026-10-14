---
kind: primary
routes:
  web: Web
steps:
- text: The Rider, the coach, hands the session to a rider in the ride
  kind: actor
  actor: rider
  entities:
  - entity: session
    effect: changes
    facts:
    - Coach
  - entity: ride
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::session
- text: The Product says on the timeline who handed it to whom
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

# Hand the session on

## Trigger

The coach has to leave early.

## Outcome

The other rider is the coach and holds the controls.

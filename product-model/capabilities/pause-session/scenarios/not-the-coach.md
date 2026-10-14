---
kind: validation
routes:
  web: Web
steps:
- text: The Rider presses Pause in a session someone else is coaching
  kind: actor
  actor: rider
  entities:
  - entity: session
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::session
- text: The Product refuses, naming the coach
  kind: product
  actor: rider
  entities:
  - entity: session
    effect: reads
    facts:
    - Coach
  contexts:
    web:
      place: web::signed-in::session
references:
- kind: code
  role: implementation
  target: server/internal/hub/channel_ride.go#refusalLocked
---

# Someone who is not the coach

## Trigger

A rider who is not coaching tries to hold the session.

## Outcome

The session runs on; being the crew's owner or an admin does not make anyone coach.

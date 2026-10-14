---
kind: validation
routes:
  web: Web
steps:
- text: The Rider arms a sprint while the session is not running, or while a game runs
  kind: actor
  actor: rider
  entities:
  - entity: session
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::session
- text: 'The Product refuses: sprints arm during a running session, and a game runs its own'
  kind: product
  actor: rider
  entities:
  - entity: session
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::session
references:
- kind: code
  role: implementation
  target: server/internal/hub/ws_messages.go
- kind: code
  role: implementation
  target: server/internal/hub/channel_ride.go#refusalLocked
---

# No running session, or a game

## Trigger

A coach arms a sprint at the wrong moment.

## Outcome

No sprint is armed.

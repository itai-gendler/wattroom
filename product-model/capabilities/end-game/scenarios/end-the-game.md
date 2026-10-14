---
kind: primary
routes:
  web: Web
steps:
- text: The Rider, the coach, ends the game
  kind: actor
  actor: rider
  entities:
  - entity: session
    effect: changes
    facts:
    - Game mode
  contexts:
    web:
      place: web::signed-in::session
- text: The Product stops the game and shows its podium
  kind: product
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::session
references:
- kind: code
  role: implementation
  target: server/internal/hub/ws_messages.go
---

# End the game

## Trigger

The crew has had enough of Floor is Lava.

## Outcome

No game runs.

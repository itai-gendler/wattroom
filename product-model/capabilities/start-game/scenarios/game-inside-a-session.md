---
kind: alternative
routes:
  web: Web
steps:
- text: The Rider, the coach, starts a game during a running workout session
  kind: actor
  actor: rider
  entities:
  - entity: session
    effect: changes
    facts:
    - Game mode
  - entity: workout
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::session
- text: The Product runs the game beside the session's timeline
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
  target: server/internal/hub/channel_game.go#startGameOn
---

# A game inside a running session

## Trigger

The coach livens up the middle of a long session.

## Outcome

The game runs inside the session.

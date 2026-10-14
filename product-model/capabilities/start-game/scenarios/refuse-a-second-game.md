---
kind: validation
routes:
  web: Web
steps:
- text: The Rider starts a game while another game runs in the channel
  kind: actor
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::voice-channel
- text: The Product refuses and says to end it first
  kind: product
  actor: rider
  entities:
  - entity: session
    effect: reads
    facts:
    - Game mode
  contexts:
    web:
      place: web::signed-in::voice-channel
references:
- kind: code
  role: implementation
  target: server/internal/hub/game.go
---

# A game is already running

## Trigger

Two members pick a game at once.

## Outcome

The running game continues.

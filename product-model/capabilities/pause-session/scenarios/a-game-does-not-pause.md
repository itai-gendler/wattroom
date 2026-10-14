---
kind: validation
routes:
  web: Web
steps:
- text: The Rider, the coach, presses Pause while a game runs
  kind: actor
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::session
- text: 'The Product refuses: a game keeps its own clock'
  kind: product
  actor: rider
  entities:
  - entity: session
    effect: reads
    facts:
    - Game mode
  contexts:
    web:
      place: web::signed-in::session
references:
- kind: code
  role: implementation
  target: server/internal/hub/channel_ride.go#refusalLocked
---

# A game keeps its own clock

## Trigger

A coach tries to pause Backyard Ramp.

## Outcome

The game runs on.

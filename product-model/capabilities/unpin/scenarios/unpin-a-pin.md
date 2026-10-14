---
kind: primary
routes:
  web: Web
steps:
- text: The Rider unpins a pin
  kind: actor
  actor: rider
  entities:
  - entity: pin
    effect: reads
    facts:
    - Title
  contexts:
    web:
      place: web::signed-in::crew-board
- text: The Product takes it off the board
  kind: product
  actor: rider
  entities:
  - entity: pin
    effect: removes
  contexts:
    web:
      place: web::signed-in::crew-board
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_pins.go#handleDeletePin
---

# Unpin

## Trigger

A pin is no longer true.

## Outcome

The pin is gone from the board.

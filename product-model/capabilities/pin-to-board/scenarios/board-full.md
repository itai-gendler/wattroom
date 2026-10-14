---
kind: edge
routes:
  web: Web
steps:
- text: The Rider pins something
  kind: actor
  actor: rider
  entities:
  - entity: pin
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-board
- text: The board already holds 20 pins
  kind: condition
  entities:
  - entity: pin
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-board
- text: The Product refuses and says to unpin one to make room
  kind: product
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::crew-board
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_pins.go#handleCreatePin
---

# A full board

## Trigger

A crew's board is full.

## Outcome

Nothing is pinned.

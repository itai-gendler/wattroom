---
kind: primary
routes:
  web: Web
steps:
- text: The Rider changes a pin's title or lines
  kind: actor
  actor: rider
  entities:
  - entity: pin
    effect: changes
    facts:
    - Title
    - Body
  contexts:
    web:
      place: web::signed-in::crew-board
- text: The Product saves the pin for every member
  kind: product
  actor: rider
  entities:
  - entity: pin
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-board
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_pins.go#handleUpdatePin
---

# Edit a pin

## Trigger

The password changed.

## Outcome

The pin says the new value.

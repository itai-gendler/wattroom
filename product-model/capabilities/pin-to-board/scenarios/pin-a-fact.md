---
kind: primary
routes:
  web: Web
steps:
- text: 'The Rider writes a title and lines such as "Password: …" and pins them'
  kind: actor
  actor: rider
  entities:
  - entity: pin
    effect: creates
    facts:
    - Title
    - Body
    - Written by
  contexts:
    web:
      place: web::signed-in::crew-board
- text: 'The Product shows the pin to every member, each Label: value line with its own copy button'
  kind: product
  actor: rider
  entities:
  - entity: pin
    effect: reads
    facts:
    - Title
    - Body
    - Written by
  contexts:
    web:
      place: web::signed-in::crew-board
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_pins.go
---

# Pin the crew's game server

## Trigger

The crew keeps asking for the same password.

## Outcome

The pin is on the board for every member.

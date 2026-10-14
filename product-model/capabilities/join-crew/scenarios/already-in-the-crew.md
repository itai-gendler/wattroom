---
kind: alternative
routes:
  web: Web
steps:
- text: The Rider opens the invite link of a crew they are already in
  kind: actor
  actor: rider
  entities:
  - entity: crew
    effect: reads
    facts:
    - Name
    - Members
  contexts:
    web:
      place: web::signed-in::crew-door
- text: The Product offers the way into the crew instead of a Join
  kind: product
  actor: rider
  entities:
  - entity: crew
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-door
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_join.go#handleCrewDoor
---

# Following your own crew's link

## Trigger

A member follows their own crew's link again.

## Outcome

Nothing changes; the rider goes straight in.

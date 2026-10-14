---
kind: validation
routes:
  web: Web
steps:
- text: The Rider opens the invite link of a crew that banned them
  kind: actor
  actor: rider
  entities:
  - entity: crew
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::signed-in::crew-door
- text: The Rider's membership in the crew is a ban
  kind: condition
  entities:
  - entity: crew-membership
    effect: reads
    facts:
    - Role
  - entity: rider
    effect: reads
    facts: []
  - entity: crew
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-door
- text: The Product says the crew removed them and offers no Join
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

# Turned away by a ban

## Trigger

A banned rider follows the crew's link or code again.

## Outcome

The rider stays out; the ban survives a new code and every other way back in.

---
kind: validation
routes:
  web: Web
steps:
- text: The Rider enters a code
  kind: actor
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::home
- text: No crew has that code
  kind: condition
  entities:
  - entity: crew
    effect: reads
    facts:
    - Invite code
  contexts:
    web:
      place: web::signed-in::home
- text: The Product says no crew has that code, or that an eight-character code is a friend code
  kind: product
  actor: rider
  entities:
  - entity: crew
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::home
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_join.go#handleJoinCrew
---

# A code no crew has

## Trigger

A rider types a wrong, old or friend's code.

## Outcome

Nothing is joined. A code the crew replaced reads the same as one that never existed.

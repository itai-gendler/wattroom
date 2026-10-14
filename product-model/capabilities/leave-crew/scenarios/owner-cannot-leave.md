---
kind: validation
routes:
  web: Web
steps:
- text: The Rider chooses Leave the crew
  kind: actor
  actor: rider
  entities:
  - entity: crew
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-home
- text: The Rider owns the crew
  kind: condition
  entities:
  - entity: crew
    effect: reads
    facts:
    - Owner
  - entity: rider
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-home
- text: The Product refuses and says to hand the crew to someone first
  kind: product
  actor: rider
  entities:
  - entity: crew
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-home
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_join.go#handleLeaveCrew
---

# The owner tries to leave

## Trigger

The crew's owner tries to leave it.

## Outcome

The owner stays; a crew is never ownerless.

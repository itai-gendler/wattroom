---
kind: edge
routes:
  web: Web
steps:
- text: The Rider asks to start a crew
  kind: actor
  actor: rider
  entities:
  - entity: crew
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::home
- text: The Rider already owns three crews they founded
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
      place: web::signed-in::home
- text: The Product refuses and says to hand one of them on to start another
  kind: product
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::home
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_found.go#handleFoundCrew
- kind: code
  role: implementation
  target: server/internal/protocol/limits.go
---

# Already owning three founded crews

## Trigger

A rider who still owns the three crews they founded tries to start a fourth.

## Outcome

No crew is created. Handing a founded crew on, or one going, frees the slot.

## Edge cases

- The Start a crew control is already disabled with the reason when the rider is at the cap.

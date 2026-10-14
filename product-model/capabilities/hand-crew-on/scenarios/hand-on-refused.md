---
kind: validation
routes:
  web: Web
steps:
- text: The Rider names someone banned from the crew, not in it, or themselves
  kind: actor
  actor: rider
  entities:
  - entity: crew
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-members
- text: The Product refuses and keeps the crew with its owner
  kind: product
  actor: rider
  entities:
  - entity: crew
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-members
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_ownership.go#handleTransferCrew
---

# Handing the crew to someone who cannot take it

## Trigger

The owner picks someone who cannot own the crew.

## Outcome

Ownership does not move.

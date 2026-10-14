---
kind: edge
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
- text: The crew has no channel left and nobody else in it but its owner
  kind: condition
  entities:
  - entity: crew
    effect: reads
    facts:
    - Members
  contexts:
    web:
      place: web::signed-in::crew-home
- text: The Product ends the Rider's membership and removes the crew with it
  kind: product
  actor: rider
  entities:
  - entity: crew
    effect: removes
  - entity: crew-membership
    effect: removes
    with: crew
  contexts:
    web:
      place: web::signed-in::crew-home
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_join.go#handleLeaveCrew
---

# The last one out of an empty crew

## Trigger

The last member leaves a crew whose owner deleted every channel.

## Outcome

The crew is gone. A crew that still has a channel never goes this way.

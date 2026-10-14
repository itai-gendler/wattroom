---
kind: primary
routes:
  web: Web
steps:
- text: The Rider chooses Leave the crew on its Home
  kind: actor
  actor: rider
  entities:
  - entity: crew
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::signed-in::crew-home
- text: The Product ends the Rider's membership and their naming into the crew's private channels
  kind: product
  actor: rider
  entities:
  - entity: crew-membership
    effect: removes
  - entity: channel-naming
    effect: removes
  - entity: crew
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-home
- text: The Product takes the Rider out of every voice channel of the crew
  kind: product
  actor: rider
  entities:
  - entity: voice-channel
    effect: changes
    facts:
    - Riders present
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

# Leave the crew

## Trigger

A member no longer wants to be in a crew.

## Outcome

The rider is no longer in the crew; a later join starts again as a Member.

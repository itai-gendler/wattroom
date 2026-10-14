---
kind: alternative
routes:
  web: Web
steps:
- text: The Rider deletes their account
  kind: actor
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::data-settings
- text: A crew the Rider owns has no one else who is not banned
  kind: condition
  entities:
  - entity: crew
    effect: reads
    facts:
    - Members
  - entity: rider
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::data-settings
- text: The Product deletes that crew with its channels, pins and plans, then the account
  kind: product
  actor: rider
  entities:
  - entity: crew
    effect: removes
  - entity: rider
    effect: removes
  - entity: pin
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::data-settings
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_ownership.go#releaseCrew
---

# A crew with nobody left

## Trigger

An owner alone in their crew leaves WattRoom.

## Outcome

Neither the crew nor the account remains.

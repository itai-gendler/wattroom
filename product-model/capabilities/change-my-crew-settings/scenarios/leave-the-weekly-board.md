---
kind: primary
routes:
  web: Web
steps:
- text: The Rider turns off their place on the crew's weekly board, or Notify me about this crew
  kind: actor
  actor: rider
  entities:
  - entity: crew-membership
    effect: changes
    facts:
    - On the weekly board
    - Notify me
  - entity: crew
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-members
- text: The Product saves the switch for this crew only
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
  target: server/internal/crews/crew_members.go#handleSetCrewPrefs
---

# Stay off the weekly board

## Trigger

A member does not want their week ranked, or their inbox filled, by one crew.

## Outcome

The switch holds for this crew; other crews keep theirs.

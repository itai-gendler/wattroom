---
kind: primary
routes:
  web: Web
steps:
- text: The Rider changes the crew's name and picks an icon
  kind: actor
  actor: rider
  entities:
  - entity: crew
    effect: changes
    facts:
    - Name
    - Icon
  contexts:
    web:
      place: web::signed-in::crew-settings
- text: The Product saves them for everyone in the crew
  kind: product
  actor: rider
  entities:
  - entity: crew
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-settings
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_write.go#handleUpdateCrew
---

# Rename the crew and pick its icon

## Trigger

The owner gives the crew its real name.

## Outcome

Every member sees the new name and icon.

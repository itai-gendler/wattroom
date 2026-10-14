---
kind: validation
routes:
  web: Web
steps:
- text: The Rider opens the crew's settings
  kind: actor
  actor: rider
  entities:
  - entity: crew
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-settings
- text: The Rider is a plain member of the crew
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
      place: web::signed-in::crew-settings
- text: The Product tells the Rider the settings are the owner's and admins', and where the roster is
  kind: product
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::crew-settings
references:
- kind: code
  role: implementation
  target: web/src/routes/(app)/crew/[id]/settings/+page.svelte
---

# A member opens the settings

## Trigger

A member reaches the crew's settings.

## Outcome

Nothing can be changed.

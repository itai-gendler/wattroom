---
kind: validation
routes:
  web: Web
steps:
- text: The Rider enters an empty name, one over 60 characters or one spanning lines
  kind: actor
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::home
- text: The Product refuses it and says a crew name is 1-60 characters on one line
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
  target: server/internal/crews/crew_found.go#cleanCrewName
---

# A crew name that is not one

## Trigger

A rider founds a crew with a name the Product does not accept.

## Outcome

No crew is created.

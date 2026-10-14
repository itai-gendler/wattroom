---
kind: alternative
routes:
  web: Web
steps:
- text: The Rider uploads a picture for the crew, or removes it
  kind: actor
  actor: rider
  entities:
  - entity: crew
    effect: changes
    facts:
    - Picture
  contexts:
    web:
      place: web::signed-in::crew-settings
- text: The Product shows it wherever the crew's mark is shown
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
  target: server/internal/crews/crew_image.go
---

# Upload a picture

## Trigger

A crew has a logo.

## Outcome

The crew's picture is set or gone.

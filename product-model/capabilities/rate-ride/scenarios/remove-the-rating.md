---
kind: alternative
routes:
  web: Web
steps:
- text: The Rider clears the rating and empties the note
  kind: actor
  actor: rider
  entities:
  - entity: ride
    effect: changes
    facts:
    - RPE
    - Note
  contexts:
    web:
      place: web::signed-in::ride-page
- text: The Product removes both; an empty note is no note
  kind: product
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::ride-page
references:
- kind: code
  role: implementation
  target: server/internal/rides/feel.go#trimNote
---

# Clear the rating

## Trigger

A rider changes their mind.

## Outcome

The ride carries neither.

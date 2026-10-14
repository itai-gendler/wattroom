---
kind: primary
routes:
  web: Web
steps:
- text: The Rider picks 7 (very hard) and writes a sentence about the ride
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
- text: The Product keeps both on the ride, for the Rider alone
  kind: product
  actor: rider
  entities:
  - entity: ride
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::ride-page
references:
- kind: code
  role: implementation
  target: server/internal/rides/feel.go
---

# Rate a ride and add a note

## Trigger

Two rides with the same watts felt nothing alike.

## Outcome

The ride carries its rating and note.

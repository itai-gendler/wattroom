---
kind: primary
routes:
  web: Web
steps:
- text: The Rider chooses to download a ride
  kind: actor
  actor: rider
  entities:
  - entity: ride
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::ride-page
- text: The Product hands them the ride as a .fit file
  kind: product
  actor: rider
  entities:
  - entity: ride
    effect: reads
    facts:
    - Started at
    - Samples
  contexts:
    web:
      place: web::signed-in::ride-page
references:
- kind: code
  role: implementation
  target: server/internal/fitexport/http.go
---

# Download the .fit file

## Trigger

A rider keeps their training log elsewhere.

## Outcome

The rider has the .fit file.

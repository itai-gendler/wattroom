---
kind: primary
routes:
  web: Web
steps:
- text: The Product offers a suggested FTP above the Rider's set one
  kind: product
  actor: rider
  entities:
  - entity: rider
    effect: reads
    facts:
    - FTP
    - Suggested FTP
  contexts:
    web:
      place: web::signed-in::ride-history
- text: The Rider chooses to use it
  kind: actor
  actor: rider
  entities:
  - entity: rider
    effect: changes
    facts:
    - FTP
    - FTP source
  contexts:
    web:
      place: web::signed-in::ride-history
references:
- kind: code
  role: implementation
  target: server/internal/protocol/limits.go
---

# Use the suggested FTP

## Trigger

A rider's fitness has outgrown their FTP.

## Outcome

Every later workout scales to the new FTP, set by the rider.

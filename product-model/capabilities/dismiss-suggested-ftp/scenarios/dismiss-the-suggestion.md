---
kind: primary
routes:
  web: Web
steps:
- text: The Rider dismisses the suggested FTP
  kind: actor
  actor: rider
  entities:
  - entity: rider
    effect: reads
    facts:
    - Suggested FTP
  contexts:
    web:
      place: web::signed-in::ride-history
- text: The Product keeps the FTP and does not offer that number again on this device
  kind: product
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::ride-history
references:
- kind: code
  role: implementation
  target: web/src/lib/suggestion-decline.ts
---

# Dismiss the suggestion

## Trigger

The rider knows the curve came from a short, unrepresentative effort.

## Outcome

The FTP is unchanged.

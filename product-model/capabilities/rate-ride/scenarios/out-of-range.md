---
kind: validation
routes:
  web: Web
steps:
- text: The Rider sends a rating outside 1–10 or a note over 500 characters
  kind: actor
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::ride-page
- text: The Product refuses it, naming the bound
  kind: product
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::ride-page
references:
- kind: code
  role: implementation
  target: server/internal/rides/feel.go#handleFeel
---

# A rating or note out of range

## Trigger

A note grows into a journal entry.

## Outcome

Nothing changes.

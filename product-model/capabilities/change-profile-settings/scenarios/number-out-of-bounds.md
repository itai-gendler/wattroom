---
kind: validation
routes:
  web: Web
steps:
- text: The Rider enters an FTP of 900 W
  kind: actor
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::profile-settings
- text: The Product refuses it, naming the field and its bounds, rather than storing another number
  kind: product
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::profile-settings
references:
- kind: code
  role: implementation
  target: server/internal/auth/me.go#handleUpdateMe
---

# A number out of bounds

## Trigger

A rider types an extra zero.

## Outcome

The FTP keeps its value.

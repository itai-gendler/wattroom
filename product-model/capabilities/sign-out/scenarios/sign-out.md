---
kind: primary
routes:
  web: Web
steps:
- text: The Rider chooses Sign out
  kind: actor
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in
- text: The Product ends the session on this device and shows the sign-in page
  kind: product
  actor: rider
  entities:
  - entity: session
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in
references:
- kind: code
  role: implementation
  target: server/internal/auth/auth.go
---

# Sign out

## Trigger

A rider is done on a shared computer.

## Outcome

This device is signed out; other devices stay signed in.

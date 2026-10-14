---
kind: primary
routes:
  web: Web
steps:
- text: The Rider, the session's coach, chooses Pause
  kind: actor
  actor: rider
  entities:
  - entity: session
    effect: changes
    from: Running
    to: Paused
    facts:
    - Elapsed
  contexts:
    web:
      place: web::signed-in::session
- text: The Product holds every joined rider's targets
  kind: product
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::session
references:
- kind: code
  role: implementation
  target: server/internal/hub/session.go
---

# Pause the session

## Trigger

Someone's doorbell rings mid-interval.

## Outcome

The timeline stands still for everyone.

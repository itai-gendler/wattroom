---
kind: primary
routes:
  web: Web
steps:
- text: The Rider, the session's coach, chooses Resume
  kind: actor
  actor: rider
  entities:
  - entity: session
    effect: changes
    from: Paused
    to: Running
    facts: []
  contexts:
    web:
      place: web::signed-in::session
- text: The Product counts down three seconds and runs the timeline from where it stood
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

# Resume the session

## Trigger

The interruption is over.

## Outcome

The timeline runs again; the workout is ridden as planned, with no block skipped.

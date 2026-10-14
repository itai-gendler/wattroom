---
kind: alternative
routes:
  web: Web
steps:
- text: The Rider, the coach, chooses End during the countdown
  kind: actor
  actor: rider
  entities:
  - entity: session
    effect: removes
    from: Counting in
  contexts:
    web:
      place: web::signed-in::session
- text: The Product clears the session and saves nothing, since nothing was ridden
  kind: product
  actor: rider
  entities:
  - entity: session
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::session
references:
- kind: code
  role: implementation
  target: server/internal/hub/session.go
---

# Stop the countdown

## Trigger

The coach started too early.

## Outcome

The channel has no session and anyone may start one.

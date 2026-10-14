---
kind: alternative
routes:
  web: Web
steps:
- text: The Rider, the crew's owner or an admin, ends a session that was picked and never started
  kind: actor
  actor: rider
  entities:
  - entity: session
    effect: removes
    from: Picked
  - entity: crew
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::voice-channel
- text: The Product clears it and saves nothing
  kind: product
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::voice-channel
references:
- kind: code
  role: implementation
  target: server/internal/hub/session.go
---

# Clear a pick left behind

## Trigger

Someone picked a workout and walked away.

## Outcome

The channel is free.

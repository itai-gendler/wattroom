---
kind: validation
routes:
  web: Web
steps:
- text: The Rider, a plain member who is not the coach, chooses End
  kind: actor
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::session
- text: 'The Product refuses: only the coach, or the crew''s owner or an admin, ends it'
  kind: product
  actor: rider
  entities:
  - entity: crew
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::session
references:
- kind: code
  role: implementation
  target: server/internal/hub/channel_ride.go#refusalLocked
---

# A member ends someone else's session

## Trigger

A rider tries to stop a session they are not running.

## Outcome

The session runs on.

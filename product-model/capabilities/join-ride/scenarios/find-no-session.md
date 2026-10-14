---
kind: validation
routes:
  web: Web
steps:
- text: The Rider asks to join the ride in a channel with no session
  kind: actor
  actor: rider
  entities:
  - entity: session
    effect: reads
    facts: []
  - entity: ride
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::session
- text: The Product says no session is running in the channel
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
  target: server/internal/hub/channel_ride.go#refusalLocked
---

# No session to join

## Trigger

The session ended a moment before.

## Outcome

Nothing is joined.

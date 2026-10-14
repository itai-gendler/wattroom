---
kind: validation
routes:
  web: Web
steps:
- text: The Rider tries to move a member who is pedalling, or into a private channel that does not name them
  kind: actor
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::voice-channel
- text: 'The Product refuses: a move would end their ride, or the channel must name them first'
  kind: product
  actor: rider
  entities:
  - entity: ride
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::voice-channel
references:
- kind: code
  role: implementation
  target: server/internal/channels/move.go#handleMove
---

# A rider who is riding

## Trigger

An admin moves someone mid-interval.

## Outcome

The member stays where they are.

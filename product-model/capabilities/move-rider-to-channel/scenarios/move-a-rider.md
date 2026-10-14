---
kind: primary
routes:
  web: Web
steps:
- text: The Rider drags a member from one voice channel onto another
  kind: actor
  actor: rider
  entities:
  - entity: voice-channel
    as: destination
    effect: reads
    facts:
    - Name
    - Riders present
  contexts:
    web:
      place: web::signed-in::voice-channel
- text: The Product moves the member there and tells them who moved them
  kind: product
  actor: rider
  entities:
  - entity: voice-channel
    as: origin
    effect: changes
    facts:
    - Riders present
  - entity: voice-channel
    as: destination
    effect: changes
    facts:
    - Riders present
  contexts:
    web:
      place: web::signed-in::voice-channel
references:
- kind: code
  role: implementation
  target: server/internal/channels/move.go#handleMove
---

# Move a rider

## Trigger

The crew splits into a fast and an easy group.

## Outcome

The member is in the other channel.

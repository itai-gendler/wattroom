---
kind: validation
routes:
  web: Web
steps:
- text: The Rider, a plain member, opens a private voice channel they are not named into
  kind: actor
  actor: rider
  entities:
  - entity: voice-channel
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::voice-channel
- text: The Product says no channel lives there
  kind: product
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::voice-channel
references:
- kind: code
  role: implementation
  target: server/internal/channels/access.go
---

# A private channel that does not name you

## Trigger

A member follows a link to a private channel.

## Outcome

The member stays out; the channel's existence is not confirmed.

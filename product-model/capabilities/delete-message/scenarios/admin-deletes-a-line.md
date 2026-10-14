---
kind: alternative
routes:
  web: Web
steps:
- text: The Rider, the crew's owner or an admin, deletes another member's line
  kind: actor
  actor: rider
  entities:
  - entity: message
    effect: removes
  - entity: crew
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::chat-channel
- text: The Product takes it out of the channel for everyone
  kind: product
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::chat-channel
references:
- kind: code
  role: implementation
  target: server/internal/chat/channel_edit.go#handleChannelDelete
---

# An admin deletes someone's line

## Trigger

An admin removes an offensive line.

## Outcome

The line is gone; its words are never logged.

---
kind: primary
routes:
  web: Web
steps:
- text: The Rider deletes a line they wrote
  kind: actor
  actor: rider
  entities:
  - entity: message
    effect: removes
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

# Delete your own line

## Trigger

An author regrets a line.

## Outcome

The line is gone.

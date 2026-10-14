---
kind: primary
routes:
  web: Web
steps:
- text: The Rider chooses Delete the chat and confirms
  kind: actor
  actor: rider
  entities:
  - entity: chat-channel
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::signed-in::crew-settings
- text: The Product deletes the channel and every message in it, for everyone
  kind: product
  actor: rider
  entities:
  - entity: chat-channel
    effect: removes
  - entity: message
    effect: removes
    with: chat-channel
  contexts:
    web:
      place: web::signed-in::crew-settings
references:
- kind: code
  role: implementation
  target: server/internal/channels/write.go#handleDelete
---

# Delete a chat channel

## Trigger

A channel has run its course.

## Outcome

The channel and its messages are gone.

---
kind: primary
routes:
  web: Web
steps:
- text: The Rider changes the words of a line they wrote
  kind: actor
  actor: rider
  entities:
  - entity: message
    effect: changes
    facts:
    - Text
  contexts:
    web:
      place: web::signed-in::chat-channel
- text: The Product shows the new words and marks the line edited
  kind: product
  actor: rider
  entities:
  - entity: message
    effect: changes
    facts:
    - Edited
  contexts:
    web:
      place: web::signed-in::chat-channel
references:
- kind: code
  role: implementation
  target: server/internal/chat/channel_edit.go#handleChannelEdit
---

# Edit your own line

## Trigger

An author spots a typo.

## Outcome

The line reads the new words and says edited.

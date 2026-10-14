---
kind: validation
routes:
  web: Web
steps:
- text: The Rider clears every word of a line that carries no picture
  kind: actor
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::chat-channel
- text: 'The Product refuses: emptying a line is deleting it'
  kind: product
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::chat-channel
references:
- kind: code
  role: implementation
  target: server/internal/chat/channel_edit.go#handleChannelEdit
---

# Editing a line to nothing

## Trigger

An author tries to blank a line rather than delete it.

## Outcome

The line keeps its words. A line with a picture may lose its words.

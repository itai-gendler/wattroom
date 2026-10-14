---
kind: validation
routes:
  web: Web
steps:
- text: The Rider sends a line with no words and no picture
  kind: actor
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::chat-channel
- text: The Product refuses it and asks them to say something first
  kind: product
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::chat-channel
references:
- kind: code
  role: implementation
  target: server/internal/chat/channel_post.go#handleChannelPost
---

# Nothing to send

## Trigger

A member presses send on an empty composer.

## Outcome

Nothing is sent.

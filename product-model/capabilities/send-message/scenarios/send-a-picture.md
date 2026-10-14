---
kind: alternative
routes:
  web: Web
steps:
- text: The Rider attaches a picture, adds words or none, and sends it
  kind: actor
  actor: rider
  entities:
  - entity: message
    effect: creates
    facts:
    - Text
    - Picture
    - Sent at
  contexts:
    web:
      place: web::signed-in::chat-channel
- text: The Product shows the picture in the channel
  kind: product
  actor: rider
  entities:
  - entity: message
    effect: reads
    facts:
    - Picture
  contexts:
    web:
      place: web::signed-in::chat-channel
references:
- kind: code
  role: implementation
  target: server/internal/chat/channel_post.go#handleChannelImageUpload
---

# Send a picture

## Trigger

A member shares a screenshot of their ride.

## Outcome

The line carries the picture. A picture uploaded and never sent goes after 15 minutes.

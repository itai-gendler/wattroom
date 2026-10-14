---
kind: primary
routes:
  web: Web
steps:
- text: The Rider takes the channel's announcement down
  kind: actor
  actor: rider
  entities:
  - entity: chat-channel
    effect: changes
    facts:
    - Announcement
  contexts:
    web:
      place: web::signed-in::chat-channel
- text: The Product removes it from the top of the channel and the Board
  kind: product
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::chat-channel
references:
- kind: code
  role: implementation
  target: server/internal/chat/channel_announcement.go
---

# Take the announcement down

## Trigger

The announced ride has happened.

## Outcome

The channel has no announcement.

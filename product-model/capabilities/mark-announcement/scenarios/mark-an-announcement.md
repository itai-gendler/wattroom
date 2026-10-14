---
kind: primary
routes:
  web: Web
steps:
- text: The Rider marks a line in the channel as its announcement
  kind: actor
  actor: rider
  entities:
  - entity: message
    effect: reads
    facts:
    - Text
  contexts:
    web:
      place: web::signed-in::chat-channel
- text: The Product puts it up at the top of the channel and of the crew's Board
  kind: product
  actor: rider
  entities:
  - entity: chat-channel
    effect: changes
    facts:
    - Announcement
  - entity: crew
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::chat-channel
references:
- kind: code
  role: implementation
  target: server/internal/chat/channel_announcement.go
- kind: doc
  role: intent
  target: docs/decisions/0057-an-announcement-is-a-chat-message-marked.md
  title: ADR-0057
---

# Mark a line as the announcement

## Trigger

An admin wants Tuesday's plan seen by everyone.

## Outcome

The line is the channel's announcement.

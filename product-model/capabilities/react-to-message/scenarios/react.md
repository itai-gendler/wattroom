---
kind: primary
routes:
  web: Web
steps:
- text: The Rider picks a reaction on a line
  kind: actor
  actor: rider
  entities:
  - entity: message
    effect: changes
    facts:
    - Reactions
  contexts:
    web:
      place: web::signed-in::chat-channel
- text: The Product shows the new total beside the line
  kind: product
  actor: rider
  entities:
  - entity: message
    effect: reads
    facts:
    - Reactions
  contexts:
    web:
      place: web::signed-in::chat-channel
references:
- kind: code
  role: implementation
  target: server/internal/chat/channel_edit.go#handleChannelReact
---

# React to a line

## Trigger

A member cheers a crew-mate's new FTP.

## Outcome

The reaction is on the line.

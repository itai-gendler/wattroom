---
kind: validation
routes:
  web: Web
steps:
- text: The Rider tries to edit a line someone else wrote
  kind: actor
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::chat-channel
- text: 'The Product refuses: only the author edits a line'
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

# Someone else's line

## Trigger

A member tries to change another member's words.

## Outcome

The line is unchanged; editing others' words is a power nobody has.

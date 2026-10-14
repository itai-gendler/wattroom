---
kind: alternative
routes:
  web: Web
steps:
- text: The Rider taps a reaction they already gave
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
- text: The Product takes it off and shows the new total
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

# Take a reaction back

## Trigger

A member reacted by mistake.

## Outcome

Their reaction is gone.

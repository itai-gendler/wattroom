---
kind: primary
routes:
  web: Web
steps:
- text: The Rider chooses Move up on a chat channel
  kind: actor
  actor: rider
  entities:
  - entity: chat-channel
    effect: changes
    facts:
    - Position
  contexts:
    web:
      place: web::signed-in::crew-settings
- text: The Product renumbers the crew's chat channels so the order has no gaps
  kind: product
  actor: rider
  entities:
  - entity: crew
    effect: reads
    facts: []
  - entity: chat-channel
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-settings
references:
- kind: code
  role: implementation
  target: server/internal/channels/write.go
---

# Move a channel up

## Trigger

An admin wants the busiest channel first.

## Outcome

Every member sees the new order.

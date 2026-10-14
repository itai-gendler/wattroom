---
kind: edge
routes:
  web: Web
steps:
- text: The Rider names a new channel
  kind: actor
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::crew-settings
- text: The crew already holds 20 chat channels or 10 voice channels
  kind: condition
  actor: rider
  entities:
  - entity: crew
    effect: reads
    facts:
    - Name
  - entity: chat-channel
    effect: reads
    facts: []
  - entity: voice-channel
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-settings
- text: The Product refuses, naming the number and saying to delete one to make room
  kind: product
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::crew-settings
references:
- kind: code
  role: implementation
  target: server/internal/channels/write.go#capOf
---

# A crew at its channel ceiling

## Trigger

A busy crew keeps adding channels.

## Outcome

No channel is added.

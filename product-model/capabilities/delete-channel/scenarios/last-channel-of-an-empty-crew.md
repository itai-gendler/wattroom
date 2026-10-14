---
kind: edge
routes:
  web: Web
steps:
- text: The Rider deletes the crew's last channel and confirms
  kind: actor
  actor: rider
  entities:
  - entity: crew
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-settings
- text: Nobody but the owner is in the crew
  kind: condition
  entities:
  - entity: crew
    effect: reads
    facts:
    - Members
  contexts:
    web:
      place: web::signed-in::crew-settings
- text: The Product deletes the channel and the crew with it, its name and invite link included
  kind: product
  actor: rider
  entities:
  - entity: crew
    effect: removes
  - entity: chat-channel
    effect: removes
    with: crew
  contexts:
    web:
      place: web::signed-in::crew-settings
references:
- kind: code
  role: implementation
  target: server/internal/channels/write.go#deleteChannel
---

# The last channel of an empty crew

## Trigger

An owner alone in their crew removes its last channel.

## Outcome

The crew is gone; the confirm said so first.

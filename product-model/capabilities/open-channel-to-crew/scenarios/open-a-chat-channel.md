---
kind: primary
routes:
  web: Web
steps:
- text: The Rider chooses Open to the crew on a private chat channel
  kind: actor
  actor: rider
  entities:
  - entity: chat-channel
    effect: changes
    facts:
    - Private
  - entity: crew
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-settings
- text: The Product lets every member of the crew enter it
  kind: product
  actor: rider
  entities:
  - entity: crew
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

# Open a chat channel

## Trigger

A private channel's talk is for everyone now.

## Outcome

Every member may enter the channel.

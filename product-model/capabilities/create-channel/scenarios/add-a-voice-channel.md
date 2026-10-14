---
kind: primary
routes:
  web: Web
steps:
- text: The Rider names a new voice channel
  kind: actor
  actor: rider
  entities:
  - entity: voice-channel
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-settings
- text: The Product adds it at the end of the crew's voice channels, open to the crew
  kind: product
  actor: rider
  entities:
  - entity: voice-channel
    effect: creates
    facts:
    - Name
    - Position
    - Private
    - Sound pack
  - entity: crew
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-settings
references:
- kind: code
  role: implementation
  target: server/internal/channels/write.go#handleCreate
---

# Add a voice channel

## Trigger

A crew wants a second room for an easy group on ride night.

## Outcome

Every member sees and may enter the new voice channel.

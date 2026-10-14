---
kind: primary
routes:
  web: Web
steps:
- text: The Rider renames a voice channel and picks Base or Silent cues
  kind: actor
  actor: rider
  entities:
  - entity: voice-channel
    effect: changes
    facts:
    - Name
    - Sound pack
  contexts:
    web:
      place: web::signed-in::crew-settings
- text: The Product saves both for everyone in the crew
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

# Rename a voice channel and pick its sound pack

## Trigger

A channel's name no longer fits, or a crew rides with the sound off.

## Outcome

The channel carries its new name and cues.

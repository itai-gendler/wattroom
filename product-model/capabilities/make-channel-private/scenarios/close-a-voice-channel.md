---
kind: primary
routes:
  web: Web
steps:
- text: The Rider chooses Make private on a voice channel
  kind: actor
  actor: rider
  entities:
  - entity: voice-channel
    effect: changes
    facts:
    - Private
  contexts:
    web:
      place: web::signed-in::crew-settings
- text: The Product takes everyone who may no longer enter out of the channel
  kind: product
  actor: rider
  entities:
  - entity: voice-channel
    effect: changes
    facts:
    - Riders present
  contexts:
    web:
      place: web::signed-in::crew-settings
references:
- kind: code
  role: implementation
  target: server/internal/channels/write.go
---

# Make a voice channel private

## Trigger

A crew wants a channel for its race team.

## Outcome

Only the owner, admins and named members may enter it.

---
kind: validation
routes:
  web: Web
steps:
- text: The Rider asks to delete a voice channel
  kind: actor
  actor: rider
  entities:
  - entity: voice-channel
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-settings
- text: A session is running in it
  kind: condition
  entities:
  - entity: session
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-settings
- text: The Product refuses and says to end the session first
  kind: product
  actor: rider
  entities:
  - entity: session
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-settings
references:
- kind: code
  role: implementation
  target: server/internal/channels/write.go#handleDelete
---

# A session is running in the channel

## Trigger

An admin deletes a channel mid-ride.

## Outcome

The channel stays; ending the session is one click for an owner or admin.

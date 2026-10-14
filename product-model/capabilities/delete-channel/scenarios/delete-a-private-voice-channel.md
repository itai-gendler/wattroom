---
kind: alternative
routes:
  web: Web
steps:
- text: The Rider chooses Delete the channel on a voice channel and confirms
  kind: actor
  actor: rider
  entities:
  - entity: voice-channel
    effect: reads
    facts:
    - Name
    - Private
  contexts:
    web:
      place: web::signed-in::crew-settings
- text: The Product deletes the channel with its recaps
  kind: product
  actor: rider
  entities:
  - entity: voice-channel
    effect: removes
  - entity: session-recap
    effect: removes
    with: voice-channel
  contexts:
    web:
      place: web::signed-in::crew-settings
references:
- kind: code
  role: implementation
  target: server/internal/channels/write.go#handleDelete
- kind: code
  role: implementation
  target: server/internal/store/queries/channels.sql#CancelPrivateChannelPlans
---

# Delete a voice channel with plans in it

## Trigger

A crew no longer rides in one of its voice channels.

## Outcome

The channel is gone.

## Decision points

### What happens to the sessions planned in it?

Was the channel private?

- Private → the plans are cancelled with it, and whoever could ride them is told.
- Open → the plans stay on the crew's schedule, naming no voice channel yet.

---
kind: primary
routes:
  web: Web
steps:
- text: The Rider opens a voice channel of their crew
  kind: actor
  actor: rider
  entities:
  - entity: voice-channel
    effect: reads
    facts:
    - Name
  - entity: crew
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::voice-channel
- text: The Product adds the Rider to the riders present and shows the session running there, if any
  kind: product
  actor: rider
  entities:
  - entity: voice-channel
    effect: changes
    facts:
    - Riders present
  - entity: session
    effect: reads
    facts:
    - Workout
    - Coach
    - Elapsed
  contexts:
    web:
      place: web::signed-in::voice-channel
references:
- kind: code
  role: implementation
  target: server/internal/hub/channel_presence.go
---

# Walk into a voice channel

## Trigger

Ride night: a member arrives in the crew's Lounge.

## Outcome

The member is present in the channel and everyone there sees them arrive.

## Edge cases

- A rider whose last connection drops is announced as gone only after a 15-second grace.

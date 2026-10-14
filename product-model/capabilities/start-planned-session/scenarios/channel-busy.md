---
kind: validation
routes:
  web: Web
steps:
- text: The Rider chooses Start now
  kind: actor
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::crew-schedule
- text: A session is already running in the plan's voice channel
  kind: condition
  actor: rider
  entities:
  - entity: session
    effect: reads
    facts:
    - Coach
  - entity: voice-channel
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-schedule
- text: The Product refuses, naming who is coaching that session
  kind: product
  actor: rider
  entities:
  - entity: session
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-schedule
references:
- kind: code
  role: implementation
  target: server/internal/hub/channel_ride.go#refusalLocked
---

# Another session holds the channel

## Trigger

Two overlapping plans name the same channel.

## Outcome

The plan stays planned; the rider knows whom to ask.

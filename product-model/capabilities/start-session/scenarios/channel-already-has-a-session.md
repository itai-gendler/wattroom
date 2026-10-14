---
kind: validation
routes:
  web: Web
steps:
- text: The Rider picks a workout in a channel where someone else is coaching a session
  kind: actor
  actor: rider
  entities:
  - entity: session
    effect: reads
    facts: []
  - entity: workout
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::voice-channel
- text: 'The Product refuses, naming the coach: one session runs in a channel at a time'
  kind: product
  actor: rider
  entities:
  - entity: session
    effect: reads
    facts:
    - Coach
  contexts:
    web:
      place: web::signed-in::voice-channel
references:
- kind: code
  role: implementation
  target: server/internal/hub/channel_ride.go#refusalLocked
---

# A session already runs here

## Trigger

A second member tries to start their own session.

## Outcome

The running session continues; the rider may join it instead.

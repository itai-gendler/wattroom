---
kind: alternative
routes:
  web: Web
steps:
- text: The Rider, present in a voice channel and in no session, sets the watts and pedals
  kind: actor
  actor: rider
  entities:
  - entity: voice-channel
    effect: reads
    facts: []
  - entity: session
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::voice-channel
- text: The Rider ends the ride, or joins a session, which saves it first
  kind: actor
  actor: rider
  entities:
  - entity: session
    effect: reads
    facts: []
  - entity: ride
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::voice-channel
- text: The Product saves the free ride
  kind: product
  actor: rider
  entities:
  - entity: ride
    effect: creates
    facts:
    - Workout
    - Started at
    - Duration
    - Average power
    - Energy
    - Scored
    - XP
    - Samples
  contexts:
    web:
      place: web::signed-in::voice-channel
references:
- kind: code
  role: implementation
  target: web/src/routes/(app)/crew/[id]/v/[channel]/training/+page.svelte
---

# Free ride in a voice channel

## Trigger

A rider warms up in the Lounge before the session starts.

## Outcome

The free ride is saved and the rider is free to join.

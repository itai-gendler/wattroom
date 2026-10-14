---
kind: primary
routes:
  web: Web
steps:
- text: The Rider names a workout and adds warm-up, steady, repeat and cooldown blocks in fractions of FTP
  kind: actor
  actor: rider
  entities:
  - entity: workout
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::workout-editor
- text: The Rider chooses Save
  kind: actor
  actor: rider
  entities:
  - entity: workout
    effect: creates
    facts:
    - Name
    - Steps
    - Length
  contexts:
    web:
      place: web::signed-in::workout-editor
- text: The Product saves it to the Rider's shelf and returns them to Workouts, ready to ride
  kind: product
  actor: rider
  entities:
  - entity: workout
    effect: reads
    facts:
    - Name
  - entity: ride
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::workout-library
references:
- kind: code
  role: implementation
  target: server/internal/customworkouts/customworkouts.go#handleCreate
---

# Build and save a workout

## Trigger

A rider wants their coach's 2×20 sweet spot session.

## Outcome

The workout is on the rider's shelf on every device.

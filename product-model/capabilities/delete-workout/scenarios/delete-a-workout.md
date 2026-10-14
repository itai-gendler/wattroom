---
kind: primary
routes:
  web: Web
steps:
- text: The Rider deletes one of their saved workouts
  kind: actor
  actor: rider
  entities:
  - entity: workout
    effect: removes
  contexts:
    web:
      place: web::signed-in::workout-library
- text: The Product takes it off the shelf; rides already ridden on it keep their numbers
  kind: product
  actor: rider
  entities:
  - entity: ride
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::workout-library
references:
- kind: code
  role: implementation
  target: server/internal/customworkouts/customworkouts.go#handleDelete
---

# Delete a saved workout

## Trigger

A rider tidies their shelf.

## Outcome

The workout is gone.

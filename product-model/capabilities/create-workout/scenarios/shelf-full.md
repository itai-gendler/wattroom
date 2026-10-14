---
kind: edge
routes:
  web: Web
steps:
- text: The Rider saves a workout
  kind: actor
  actor: rider
  entities:
  - entity: workout
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::workout-editor
- text: The Rider already keeps 200 saved workouts
  kind: condition
  entities:
  - entity: workout
    effect: reads
    facts: []
  - entity: rider
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::workout-editor
- text: The Product refuses, naming the number and saying to delete one
  kind: product
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::workout-editor
references:
- kind: code
  role: implementation
  target: server/internal/customworkouts/customworkouts.go#handleCreate
---

# A full shelf

## Trigger

A rider has saved a great many workouts.

## Outcome

Nothing is saved.

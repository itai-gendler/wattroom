---
kind: validation
routes:
  web: Web
steps:
- text: The Rider drops a file the Product cannot read as a workout
  kind: actor
  actor: rider
  entities:
  - entity: workout
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::workout-import
- text: The Product says it could not read the file
  kind: product
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::workout-import
references:
- kind: code
  role: implementation
  target: web/src/routes/(app)/workouts/import/+page.svelte
---

# A file that is not a workout

## Trigger

A rider picks the wrong file.

## Outcome

Nothing is imported.

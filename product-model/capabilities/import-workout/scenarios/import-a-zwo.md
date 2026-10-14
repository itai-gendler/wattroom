---
kind: primary
routes:
  web: Web
steps:
- text: The Rider drops a .zwo file on Import
  kind: actor
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::workout-import
- text: The Product previews it at the Rider's FTP
  kind: product
  actor: rider
  entities:
  - entity: rider
    effect: reads
    facts:
    - FTP
  contexts:
    web:
      place: web::signed-in::workout-import
- text: The Rider saves it
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
      place: web::signed-in::workout-import
references:
- kind: code
  role: implementation
  target: web/src/routes/(app)/workouts/import/+page.svelte
---

# Import a .zwo file

## Trigger

A rider brings the .zwo workouts they already have.

## Outcome

The workout is on their shelf.

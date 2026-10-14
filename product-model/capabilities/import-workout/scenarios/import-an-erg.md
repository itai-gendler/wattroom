---
kind: alternative
routes:
  web: Web
steps:
- text: The Rider drops an .erg file written in watts
  kind: actor
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::workout-import
- text: The Product converts its watts into fractions of the Rider's FTP at the time of import
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

# Import an .erg file in watts

## Trigger

A rider has a power-based file from another trainer app.

## Outcome

The workout is on their shelf, scaled to their FTP.

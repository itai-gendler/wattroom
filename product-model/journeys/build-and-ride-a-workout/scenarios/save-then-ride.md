---
kind: primary
result: achieved
routes:
  web: Web
steps:
- text: The Rider builds a workout in the editor and saves it
  kind: actor
  actor: rider
  capability: create-workout
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
- text: The Product returns the Rider to Workouts with the new workout ready to ride
  kind: product
  actor: rider
  capability: create-workout
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
- text: The Rider chooses to ride the new workout
  kind: actor
  actor: rider
  capability: ride-workout-alone
  entities:
  - entity: workout
    effect: reads
    facts:
    - Name
    - Steps
  - entity: ride
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::workout-library
- text: The Product opens the ride with that workout at the Rider's FTP
  kind: product
  actor: rider
  capability: ride-workout-alone
  entities:
  - entity: rider
    effect: reads
    facts:
    - FTP
  - entity: ride
    effect: reads
    facts: []
  - entity: workout
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::ride-alone
references:
- kind: code
  role: implementation
  target: web/src/routes/(app)/workouts/edit/+page.svelte
---

# Save, then ride it

## Trigger

A rider writes the session their coach prescribed.

## Outcome

The rider is riding the workout they just built.

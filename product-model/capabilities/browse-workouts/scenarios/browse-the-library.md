---
kind: primary
routes:
  web: Web
steps:
- text: The Rider opens Workouts
  kind: actor
  actor: rider
  entities:
  - entity: workout
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::workout-library
- text: The Product lists the curated library and the Rider's saved workouts, previewed at the Rider's FTP
  kind: product
  actor: rider
  entities:
  - entity: workout
    effect: reads
    facts:
    - Name
    - Steps
    - Length
  - entity: rider
    effect: reads
    facts:
    - FTP
  contexts:
    web:
      place: web::signed-in::workout-library
references:
- kind: code
  role: implementation
  target: server/internal/customworkouts/customworkouts.go
---

# Browse the library and your shelf

## Trigger

A rider looks for tonight's workout.

## Outcome

The rider sees what they can ride and how hard it is for them.

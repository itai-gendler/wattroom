---
kind: validation
routes:
  web: Web
steps:
- text: The Rider builds a step out of bounds, such as a cadence floor at or under 50 rpm or a heart-rate hold with no band
  kind: actor
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::workout-editor
- text: The Product marks the step and keeps Save from saving it
  kind: product
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::workout-editor
references:
- kind: code
  role: implementation
  target: server/internal/workout/validate.go
---

# A workout the engine cannot ride

## Trigger

A rider writes a step that fights a safety guard.

## Outcome

Nothing is saved until the step is fixed.

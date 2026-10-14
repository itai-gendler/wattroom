---
appliesTo:
- type: entity
  id: workout
  effect: removes
permits:
- related:
  - verb: owns
    entity: rider
references:
- kind: code
  role: implementation
  target: server/internal/customworkouts/customworkouts.go#handleDelete
---

# Only the rider deletes their saved workouts

The curated library ships with the app and is nobody's to delete.

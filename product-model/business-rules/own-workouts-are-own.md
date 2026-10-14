---
appliesTo:
- type: entity
  id: workout
  effect: changes
  facts:
  - Name
  - Steps
  - Length
permits:
- related:
  - verb: owns
    entity: rider
references:
- kind: code
  role: implementation
  target: server/internal/customworkouts/customworkouts.go
---

# Only the rider changes and deletes their saved workouts

Someone else's workout reads as absent.

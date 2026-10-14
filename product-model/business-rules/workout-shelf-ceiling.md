---
appliesTo:
- type: capability
  id: create-workout
- type: capability
  id: import-workout
- type: entity
  id: workout
references:
- kind: code
  role: implementation
  target: server/internal/customworkouts/customworkouts.go
- kind: doc
  role: intent
  target: docs/spec/roles.md
  title: 'Spec: roles and permissions'
---

# A rider keeps at most 200 saved workouts

The ceiling is refused naming the number and the remedy; it never clears on its own.

---
appliesTo:
- type: capability
  id: start-session
- type: capability
  id: plan-session
- type: entity
  id: workout
references:
- kind: code
  role: implementation
  target: server/internal/workout/validate.go
- kind: doc
  role: intent
  target: docs/spec/workouts.md
  title: 'Spec: HR hold'
---

# A workout that holds heart rate is ridden alone

A session, and a plan, refuses a workout with a heart-rate hold step, and says why in one line.

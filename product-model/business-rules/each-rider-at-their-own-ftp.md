---
appliesTo:
- type: capability
  id: start-session
- type: capability
  id: join-ride
- type: capability
  id: ride-workout-alone
- type: entity
  id: session
references:
- kind: doc
  role: intent
  target: docs/spec/workouts.md
  title: 'Spec: workout JSON'
- kind: doc
  role: intent
  target: docs/spec/stats.md
  title: 'Spec: tolerance band'
---

# Every rider rides a workout at their own share of their own FTP

Targets are fractions of FTP, and each trainer holds its own rider's share in ERG mode; execution is judged against the rider's own target.

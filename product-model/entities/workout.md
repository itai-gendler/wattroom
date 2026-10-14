---
domain: workouts
references:
- kind: code
  role: implementation
  target: server/internal/customworkouts/customworkouts.go
- kind: code
  role: implementation
  target: server/internal/workout/validate.go
- kind: doc
  role: intent
  target: docs/spec/workouts.md
  title: 'Spec: workout JSON'
---

# Workout

A workout a rider saved to their own shelf, built in the editor or imported. The curated library ships with the app and is not kept per rider.

## Information kept

- **Name** — 1–80 characters
- **Steps** — warm-up, steady, ramp, repeat, cooldown and sprint blocks, as fractions of FTP or in watts, with optional cadence and heart-rate bands
- **Length** — how long it runs, between a second and a day

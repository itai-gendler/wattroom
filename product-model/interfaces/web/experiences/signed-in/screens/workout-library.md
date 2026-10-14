---
entities:
- entity: ride
  shows:
  - Workout
- entity: rider
  shows:
  - FTP
- entity: workout
  shows:
  - Length
  - Name
  - Steps
entryPoints:
- web: /workouts
references:
- kind: code
  role: implementation
  target: web/src/routes/(app)/workouts/+page.svelte
---

# Workout library

The curated library and the rider's own saved workouts, each previewed at the rider's FTP.

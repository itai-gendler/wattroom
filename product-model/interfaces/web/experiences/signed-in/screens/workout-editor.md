---
entities:
- entity: workout
  collects:
  - Length
  - Name
  - Steps
entryPoints:
- web: /workouts/edit
references:
- kind: code
  role: implementation
  target: web/src/routes/(app)/workouts/edit/+page.svelte
---

# Workout editor

Where a rider builds a workout block by block.

---
entities:
- entity: rider
  shows:
  - FTP
- entity: workout
  collects:
  - Length
  - Name
  - Steps
entryPoints:
- web: /workouts/import
references:
- kind: code
  role: implementation
  target: web/src/routes/(app)/workouts/import/+page.svelte
---

# Workout import

Where a rider brings in a .zwo or .erg file as a workout of their own.

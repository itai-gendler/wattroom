---
availability:
- place: web::signed-in
domain: workouts
references:
- kind: code
  role: implementation
  target: web/src/routes/(app)/workouts/import/+page.svelte
---

# Import a workout

A rider brings in a .zwo or .erg file they already have; it becomes an ordinary workout on their shelf, saved the way the editor saves.

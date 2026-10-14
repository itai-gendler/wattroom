---
availability:
- place: web::signed-in
domain: workouts
references:
- kind: code
  role: implementation
  target: web/src/routes/(app)/workouts/edit/+page.svelte
- kind: code
  role: implementation
  target: server/internal/customworkouts/customworkouts.go#handleCreate
---

# Create a workout

A rider builds a workout block by block in the editor and saves it to their shelf. Validation is inline, so Save never surprises.

---
availability:
- place: web::signed-in
domain: workouts
references:
- kind: code
  role: implementation
  target: web/src/routes/(app)/workouts/+page.svelte
- kind: code
  role: implementation
  target: server/internal/customworkouts/customworkouts.go#handleList
---

# Browse workouts

A rider browses the curated library and their own saved workouts, each previewed at their own FTP, and picks one to ride.

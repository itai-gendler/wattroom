---
availability:
- place: web::signed-in
domain: workouts
references:
- kind: code
  role: implementation
  target: server/internal/customworkouts/customworkouts.go#handleDelete
---

# Delete a workout

A rider takes a workout off their shelf.

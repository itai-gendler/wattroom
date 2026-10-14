---
availability:
- place: web::signed-in
domain: workouts
references:
- kind: code
  role: implementation
  target: server/internal/customworkouts/customworkouts.go#handleUpdate
---

# Edit a workout

A rider changes one of their saved workouts in the editor.

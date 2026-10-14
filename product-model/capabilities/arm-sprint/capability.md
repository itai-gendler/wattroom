---
availability:
- place: web::signed-in
domain: voice-channels
references:
- kind: code
  role: implementation
  target: server/internal/hub/sprint.go
- kind: code
  role: implementation
  target: server/internal/hub/channel_sprint.go
---

# Arm a sprint

The coach arms a sprint moment in a running session: a klaxon three seconds before, a 15-second all-out window, and a podium ranked on best 5-second w/kg.

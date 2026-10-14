---
availability:
- place: web::signed-in
domain: voice-channels
references:
- kind: code
  role: implementation
  target: server/internal/hub/session.go
- kind: code
  role: implementation
  target: server/internal/hub/channel_ride.go#refusalLocked
---

# Pause a session

The session's coach holds the shared timeline.

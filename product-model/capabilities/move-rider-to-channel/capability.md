---
availability:
- place: web::signed-in
domain: voice-channels
references:
- kind: code
  role: implementation
  target: server/internal/channels/move.go#handleMove
---

# Move a rider to another voice channel

The crew's owner or an admin moves a rider from one of the crew's voice channels into another, call and all, as long as the rider is not pedalling and the destination admits them.

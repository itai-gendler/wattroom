---
availability:
- place: web::signed-in
domain: voice-channels
references:
- kind: code
  role: implementation
  target: server/internal/hub/channel_ride.go#handOffLocked
---

# Hand the session on

The coach hands the session to someone riding in it: a light, live act that changes no crew role.

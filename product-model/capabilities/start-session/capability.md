---
availability:
- place: web::signed-in
domain: voice-channels
references:
- kind: code
  role: implementation
  target: server/internal/hub/channel_ride.go#controlOn
- kind: code
  role: implementation
  target: server/internal/hub/session.go
- kind: doc
  role: intent
  target: docs/spec/roles.md
  title: 'Spec: session lifecycle'
---

# Start a session

Someone present in a voice channel picks a workout and starts a session, becoming its coach. After a 10-second countdown the shared timeline runs, and every joined rider's trainer holds that rider's own share of their FTP.

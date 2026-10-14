---
availability:
- place: web::signed-in
domain: voice-channels
references:
- kind: code
  role: implementation
  target: server/internal/hub/session_end.go
- kind: code
  role: implementation
  target: server/internal/stats/saver.go#SaveSession
- kind: code
  role: implementation
  target: server/internal/stats/medals.go#Medals
---

# End a session

A session ends when its timeline runs out, when its coach ends it, or when the crew's owner or an admin ends one somebody left running. The Product then saves every joined rider's ride of at least a minute, awards medals, keeps a recap and pays XP.

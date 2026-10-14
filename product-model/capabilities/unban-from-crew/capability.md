---
availability:
- place: web::signed-in
domain: members
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_write.go#handleSetCrewRole
---

# Unban a rider

The crew's owner or an admin lifts a ban. Lifting it restores plain membership; it reconnects nobody and gives back no private channel.

---
availability:
- place: web::signed-in
domain: crew-settings
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_write.go#handleRotateCrewCode
---

# Make a new invite link

The crew's owner or an admin makes a new invite code. The old code, and every link carrying it, stops working at once.

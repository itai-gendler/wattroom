---
availability:
- place: web::signed-in
domain: members
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_write.go#handleSetCrewRole
---

# Ban a rider from a crew

The crew's owner or an admin bans a rider. The ban is the crew's one ban: it keeps the seat so it survives a new code and every way back in, takes the rider out of every voice channel at once, and drops their naming into private channels. A rider not yet in the crew may be banned ahead.

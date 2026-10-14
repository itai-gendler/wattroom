---
availability:
- place: web::signed-in
domain: members
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_write.go#handleSetCrewRole
---

# Make an admin a member again

The crew's owner or an admin takes the admin role back, leaving a plain member. A demoted admin drops out of the private channels that no longer admit them.

---
availability:
- place: web::signed-in
domain: members
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_write.go#handleSetCrewRole
- kind: code
  role: implementation
  target: web/src/routes/(app)/crew/[id]/members/CrewPeople.svelte
---

# Make a member an admin

The crew's owner or an admin makes a member a crew admin, who then keeps the crew's settings, channels and members beside the owner.

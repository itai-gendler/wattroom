---
availability:
- place: web::signed-in
domain: members
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_members.go#handleCrewMembers
- kind: code
  role: implementation
  target: web/src/routes/(app)/crew/[id]/members/+page.svelte
---

# View a crew's members

A member opens the crew's Members page: the roster with each person's role, the day they joined and the medals the crew's sessions awarded them, the crew streak, the weekly board while the crew keeps one, and the recaps of its sessions. The crew's owner and admins see the whole crew and its ban list; a plain member sees the crew's owner and the crew-mates they share a channel with.

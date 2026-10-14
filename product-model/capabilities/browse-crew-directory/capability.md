---
availability:
- place: web::signed-in
domain: crews
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_directory.go#handleCrewDirectory
- kind: code
  role: implementation
  target: web/src/routes/(app)/crews/directory/+page.svelte
---

# Find a crew

A rider browses the directory of crews their owners or admins chose to list: a name, a mark and the way to its door. Joining from the directory goes through the crew's door like any invite.

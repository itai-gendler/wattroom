---
availability:
- place: web::signed-in
domain: crew-settings
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_write.go#handleUpdateCrew
- kind: code
  role: implementation
  target: server/internal/crews/crew_image.go
- kind: code
  role: implementation
  target: web/src/routes/(app)/crew/[id]/settings/+page.svelte
---

# Change crew settings

The crew's owner or an admin changes its name, icon and picture, lists it in the directory, and turns its weekly board on or off. Every control saves on change.

---
availability:
- place: web::signed-in
domain: crew-settings
references:
- kind: code
  role: implementation
  target: server/internal/channels/write.go
- kind: code
  role: implementation
  target: server/internal/channels/reauthorize.go
---

# Make a channel private

The crew's owner or an admin makes an open channel private. It then admits only the owner, the admins and the members named into it, and anyone else is shut out at once, call and all.

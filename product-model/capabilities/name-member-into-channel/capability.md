---
availability:
- place: web::signed-in
domain: crew-settings
references:
- kind: code
  role: implementation
  target: server/internal/channels/members.go#handleNameMember
---

# Name a member into a private channel

The crew's owner or an admin names a member into a private channel, which lets them enter it. Naming someone twice names them once.

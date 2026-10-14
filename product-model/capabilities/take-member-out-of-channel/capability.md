---
availability:
- place: web::signed-in
domain: crew-settings
references:
- kind: code
  role: implementation
  target: server/internal/channels/members.go#handleUnnameMember
---

# Take a member out of a private channel

The crew's owner or an admin takes a named member back out of a private channel.

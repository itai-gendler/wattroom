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
  target: web/src/routes/(app)/crew/[id]/settings/ChannelRow.svelte
---

# Move a channel

The crew's owner or an admin moves a channel up or down its list.

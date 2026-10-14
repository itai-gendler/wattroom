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

# Edit a channel

The crew's owner or an admin renames a channel, and sets a voice channel's sound pack.

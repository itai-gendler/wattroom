---
availability:
- place: web::signed-in
domain: crew-settings
references:
- kind: code
  role: implementation
  target: server/internal/channels/write.go#handleCreate
- kind: code
  role: implementation
  target: web/src/routes/(app)/crew/[id]/settings/CrewChannels.svelte
---

# Create a channel

The crew's owner or an admin adds a chat channel or a voice channel, open to the crew or private from the start.

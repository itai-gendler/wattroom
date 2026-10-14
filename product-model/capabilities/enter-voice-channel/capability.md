---
availability:
- place: web::signed-in
domain: voice-channels
references:
- kind: code
  role: implementation
  target: server/internal/channels/access.go#mayEnter
- kind: code
  role: implementation
  target: server/internal/hub/ws.go
- kind: code
  role: implementation
  target: web/src/routes/(app)/crew/[id]/v/[channel]/+page.svelte
---

# Enter a voice channel

A member walks into a voice channel they may enter: an open one, or a private one that admits them. They are present there, see who else is and whether a session runs, and from there ride, talk and watch.

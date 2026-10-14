---
availability:
- place: web::signed-in
domain: voice-channels
references:
- kind: code
  role: implementation
  target: server/internal/hub/channel_ride.go#controlOn
- kind: code
  role: implementation
  target: web/src/routes/(app)/crew/[id]/s/[session]/+page.svelte
---

# Join the ride

Someone in a voice channel with a session running joins its ride. They ride the session's current block at their own share of FTP, synced to where the shared timeline stands.

---
entities:
- entity: chat-channel
  shows:
  - Name
  collects:
  - Announcement
- entity: crew
  shows:
  - Name
- entity: message
  shows:
  - Disappears at
  - Picture
  - Reactions
  - Sent at
  - Text
  collects:
  - Disappears at
  - Picture
  - Reactions
  - Sent at
  - Text
entryPoints:
- web: /crew/{id}/c/{channel}
references:
- kind: code
  role: implementation
  target: web/src/routes/(app)/crew/[id]/c/[channel]/+page.svelte
---

# Chat channel

One chat channel's conversation, with its announcement on top.

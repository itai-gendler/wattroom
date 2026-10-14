---
availability:
- place: web::signed-in
domain: chat
references:
- kind: code
  role: implementation
  target: server/internal/chat/channel_announcement.go#handleClearChannelAnnouncement
---

# Remove an announcement

The crew's owner or an admin takes a channel's announcement down. The line stays in the channel as an ordinary message.

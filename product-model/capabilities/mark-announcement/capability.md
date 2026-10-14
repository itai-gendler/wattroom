---
availability:
- place: web::signed-in
domain: chat
references:
- kind: code
  role: implementation
  target: server/internal/chat/channel_announcement.go#handleSetChannelAnnouncement
---

# Mark an announcement

The crew's owner or an admin marks a line as the channel's announcement. It leads the channel and the crew's Board, and the 500-message bound keeps it.

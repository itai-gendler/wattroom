---
availability:
- place: web::signed-in
domain: chat
references:
- kind: code
  role: implementation
  target: server/internal/chat/channel_edit.go#handleChannelDelete
---

# Delete a message

An author deletes their own line; the crew's owner and admins delete any line. A deleted line vanishes from the channel.

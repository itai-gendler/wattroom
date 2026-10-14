---
availability:
- place: web::signed-in
domain: chat
references:
- kind: code
  role: implementation
  target: server/internal/chat/channel_edit.go#handleChannelEdit
---

# Edit a message

An author changes the words of their own line, for as long as the line exists. Every edited line says edited.

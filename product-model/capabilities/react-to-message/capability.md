---
availability:
- place: web::signed-in
domain: chat
references:
- kind: code
  role: implementation
  target: server/internal/chat/channel_edit.go#handleChannelReact
---

# React to a message

Someone in a chat channel puts a reaction on a line, from their own reaction set, any emoji or the crew's own, and takes it off again with the same tap.

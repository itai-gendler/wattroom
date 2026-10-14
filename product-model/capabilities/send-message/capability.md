---
availability:
- place: web::signed-in
domain: chat
references:
- kind: code
  role: implementation
  target: server/internal/chat/channel_post.go
- kind: doc
  role: intent
  target: docs/spec/crew.md
  title: 'Spec: text channel chat'
---

# Send a message

Someone who may enter a chat channel writes a line there, with a picture if they like, and may make it temporary. Every send keeps the channel's last 500 messages and lets older ones go, except the channel's announcement.

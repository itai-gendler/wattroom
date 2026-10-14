---
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

# Message

A line someone wrote in a chat channel. A channel keeps its last 500 messages.

## Information kept

- **Text** — 1–500 characters; may be empty only when the line carries a picture
- **Picture** — an image attached to the line
- **Sent at** — when the line was sent
- **Edited** — whether the author changed the line since sending it
- **Disappears at** — for a temporary line, when it goes: 1 hour, 24 hours or 7 days after it was sent
- **Reactions** — the reactions on the line and who gave each

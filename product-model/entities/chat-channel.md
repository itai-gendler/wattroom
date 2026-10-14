---
domain: chat
relations:
- entity: message
  verb: holds
  cardinality: one-to-many
- entity: channel-naming
  verb: names
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: server/internal/channels/write.go
- kind: code
  role: implementation
  target: server/internal/chat/channel_announcement.go
---

# Chat channel

A crew's text channel: a conversation for the week, open to the crew or private to the members named into it.

## Information kept

- **Name** — 1–60 characters on one line
- **Position** — its place in the crew's list of chat channels
- **Private** — whether only the crew's owner, its admins and the members named into it may enter
- **Announcement** — the one message marked as the channel's announcement, if any

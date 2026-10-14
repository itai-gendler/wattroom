---
domain: voice-channels
relations:
- entity: session
  verb: runs
  cardinality: one-to-many
- entity: planned-session
  verb: hosts
  cardinality: one-to-many
- entity: session-recap
  verb: keeps
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
  target: server/internal/channels/access.go#mayEnter
---

# Voice channel

A crew's place to ride: its call, the riders present, and at most one session at a time. Open to the crew or private to the members named into it.

## Information kept

- **Name** — 1–60 characters on one line
- **Position** — its place in the crew's list of voice channels
- **Private** — whether only the crew's owner, its admins and the members named into it may enter
- **Sound pack** — the cues the channel plays: Base, or Silent with visual cues only
- **Riders present** — who is in the channel now, and who is riding

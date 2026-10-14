---
domain: members
references:
- kind: code
  role: implementation
  target: server/internal/recap/recap.go
- kind: doc
  role: intent
  target: docs/spec/crew.md
  title: 'Spec: session recap retention'
---

# Session recap

What a finished session leaves its crew: who was in the voice channel, when they arrived, how long they stayed and whether they rode. Presence and time only, kept 90 days.

## Information kept

- **Workout** — what the session rode
- **Started at** — when the session started
- **Who was there** — each person in the channel's voice, when they arrived, how long they stayed and whether they rode

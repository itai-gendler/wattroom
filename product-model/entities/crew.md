---
domain: crews
relations:
- entity: crew-membership
  verb: has
  cardinality: one-to-many
- entity: chat-channel
  verb: holds
  cardinality: one-to-many
- entity: voice-channel
  verb: holds
  cardinality: one-to-many
- entity: planned-session
  verb: keeps
  cardinality: one-to-many
- entity: pin
  verb: keeps
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: server/internal/crews/crews.go
- kind: doc
  role: intent
  target: docs/spec/roles.md
  title: 'Spec: the crew, its owner and its channels'
---

# Crew

The people who ride together, and the place they do it: a name and a mark, its members and their roles, its chat and voice channels, its schedule, its pins and its weekly board. A crew is reached by its invite code, or from the directory once it is listed.

## Information kept

- **Name** — 1–60 characters on one line
- **Icon** — one drawn icon from a curated set, or none
- **Picture** — an optional uploaded picture beside the icon
- **Invite code** — six characters; the crew's code and share link, and the only door in
- **Owner** — the one rider whose crew it is; never more than one and never none
- **Listed in directory** — whether the crew appears in the directory of crews; off until its owner or an admin lists it
- **Weekly board** — whether the crew shows a weekly board of its members' riding; off until its owner or an admin turns it on
- **Members** — how many people are in the crew
- **Crew streak** — consecutive UTC weeks in which someone rode in one of its voice channels

---
domain: board
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_pins.go
- kind: doc
  role: intent
  target: docs/spec/glossary.md
  title: 'Glossary: Pin'
---

# Pin

A title and a block of lines on a crew's board: a fact the crew keeps needing, such as a server password or a door code. Every member reads and writes pins.

## Information kept

- **Title** — 1–40 characters
- **Body** — 1–1000 characters; a line written "Label: value" reads as a row of its own
- **Written by** — the member who wrote it, while their account exists

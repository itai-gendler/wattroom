---
appliesTo:
- type: capability
  id: pin-to-board
- type: entity
  id: pin
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_pins.go
- kind: doc
  role: intent
  target: docs/spec/glossary.md
  title: 'Glossary: Pin'
---

# A crew's board holds at most 20 pins

Every member pins, edits and unpins; nothing records who changed a pin, and a pin is not a secret: every member reads it.

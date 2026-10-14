---
appliesTo:
- type: capability
  id: found-crew
- type: entity
  id: crew
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_found.go
- kind: doc
  role: intent
  target: docs/spec/roles.md
  title: 'Spec: roles and permissions'
---

# A rider founds at most three crews

Counted over the crews they founded and still own, so handing one on frees the slot, and so does one going. A rider may still come to own more when one is handed to them.

---
availability:
- place: web::signed-in
domain: members
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_members.go#handleSetCrewPrefs
- kind: code
  role: implementation
  target: web/src/lib/components/RiderPrefs.svelte
---

# Change your settings for a crew

A member sets their own switches for one crew on its Members page: whether its planned sessions notify them, and whether their week appears on its weekly board. Nobody else changes them.

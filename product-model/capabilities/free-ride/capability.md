---
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: web/src/routes/(app)/crew/[id]/v/[channel]/training/+page.svelte
- kind: code
  role: implementation
  target: server/internal/rides/save.go
- kind: doc
  role: intent
  target: docs/spec/roles.md
  title: 'Spec: the free ride'
---

# Free ride

A rider rides with no timeline: they set the grade, from −5 % to +15 % in half-percent steps, or the watts, from 50 W to 1000 W in 10 W steps, and shift virtual gears on the grade. It records from the first pedal stroke to End ride and is saved as "Free ride", unscored. A rider free-rides alone or in a voice channel beside whatever runs there.

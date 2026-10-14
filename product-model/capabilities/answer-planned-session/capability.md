---
availability:
- place: web::signed-in
domain: schedule
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_schedule.go#handleCrewRsvp
- kind: code
  role: implementation
  target: web/src/lib/session/RsvpRow.svelte
---

# Answer a planned session

A member says they are in or out for a plan, changes their mind with one tap, or takes their answer back. There is no maybe.

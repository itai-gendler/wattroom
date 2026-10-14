---
availability:
- place: web::signed-in
domain: schedule
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_schedule.go#handleCrewSchedule
- kind: code
  role: implementation
  target: web/src/routes/(app)/crew/[id]/schedule/+page.svelte
---

# Read the crew's schedule

A member reads the crew's planned sessions in start order, each with who is in by name and how many are out or have not answered. A plan whose time passed unstarted stays for 30 minutes, then drops off.

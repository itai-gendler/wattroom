---
availability:
- place: web::signed-in
domain: schedule
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_schedule.go#handleCrewMove
---

# Move a planned session

The plan's planner, or the crew's owner or an admin, moves a plan to a new time. A real move asks again everyone who said they were out; an "in" survives it.

---
availability:
- place: web::signed-in
domain: schedule
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_schedule.go
---

# Cancel a planned session

The plan's planner, or the crew's owner or an admin, cancels a plan that has not started. The crew is told, whatever anyone answered.

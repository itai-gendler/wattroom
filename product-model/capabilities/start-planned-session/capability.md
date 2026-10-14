---
availability:
- place: web::signed-in
domain: schedule
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_schedule.go#handleCrewStarted
- kind: code
  role: implementation
  target: web/src/lib/crew-schedule.ts#planDue
---

# Start a planned session

Someone who may enter the plan's voice channel chooses Start now on a plan from 15 minutes before its time until 30 minutes after. The session opens in that channel with them as its coach, the plan's workout picked and counting in, and the plan leaves the schedule.

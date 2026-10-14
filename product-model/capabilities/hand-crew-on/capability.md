---
availability:
- place: web::signed-in
domain: members
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_ownership.go#handleTransferCrew
---

# Hand the crew on

The owner hands the crew to someone in it, after confirming. The new owner's own role is settled, since owner beats it, and the previous owner stays on as an admin.

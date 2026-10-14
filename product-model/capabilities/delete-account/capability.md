---
availability:
- place: web::signed-in
domain: settings
references:
- kind: code
  role: implementation
  target: server/internal/account/delete.go
- kind: code
  role: implementation
  target: server/internal/crews/crew_ownership.go#ReleaseCrews
- kind: code
  role: implementation
  target: web/src/lib/profile/YourData.svelte
---

# Delete your account

A rider deletes their account after typing a confirmation phrase. Every crew they own passes to its longest-standing admin, else its longest-standing member, or goes when nobody is left; their rides, workouts and memberships go with the account.

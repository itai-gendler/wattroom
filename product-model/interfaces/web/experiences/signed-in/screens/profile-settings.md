---
entities:
- entity: rider
  collects:
  - FTP
  - FTP source
  - Weight
  - Weight source
entryPoints:
- web: /settings/profile
references:
- kind: code
  role: implementation
  target: web/src/routes/(app)/settings/profile/+page.svelte
---

# Profile settings

The rider's profile: display name, picture, FTP, weight and threshold heart rate.

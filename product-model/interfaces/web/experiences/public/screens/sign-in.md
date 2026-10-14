---
entities:
- entity: rider
  shows:
  - Sign-in methods
entryPoints:
- web: /login
references:
- kind: code
  role: implementation
  target: web/src/routes/(app)/login/+page.svelte
---

# Sign in

Where a person signs in with Google, GitHub, Strava or a passkey; every other address sends a signed-out person here first.

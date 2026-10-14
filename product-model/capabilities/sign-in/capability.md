---
availability:
- place: web::public
references:
- kind: code
  role: implementation
  target: server/internal/auth/providers.go#providersFromEnv
- kind: code
  role: implementation
  target: server/internal/auth/callback.go
- kind: code
  role: implementation
  target: server/internal/auth/passkey.go
- kind: code
  role: implementation
  target: web/src/routes/(app)/login/+page.svelte
- kind: doc
  role: intent
  target: docs/decisions/0009-login-gated-app.md
  title: ADR-0009
---

# Sign in

A person signs in with Google, GitHub or Strava, which creates their account the first time, or with a passkey they added to an existing account. Only the providers the deployment has configured are offered.

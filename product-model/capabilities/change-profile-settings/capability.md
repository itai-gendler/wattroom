---
availability:
- place: web::signed-in
domain: settings
references:
- kind: code
  role: implementation
  target: server/internal/auth/me.go#handleUpdateMe
- kind: code
  role: implementation
  target: web/src/routes/(app)/settings/profile/+page.svelte
- kind: doc
  role: intent
  target: docs/spec/stats.md
  title: 'Spec: the rider''s two numbers'
---

# Change profile settings

A rider sets their display name, picture, FTP, weight and threshold heart rate. FTP and weight are what every target and every w/kg are relative to, and a number the rider set is told apart from the starting guess.

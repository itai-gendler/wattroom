---
kind: primary
routes:
  web: Web
steps:
- text: The Visitor chooses Continue with Google, Continue with GitHub or Connect with Strava and agrees at the provider
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: web::public::sign-in
- text: The Product creates an account from the provider's name and picture, starting at 200 W and 75 kg that nobody has chosen yet
  kind: product
  actor: visitor
  entities:
  - entity: rider
    effect: creates
    facts:
    - Display name
    - Picture
    - Sign-in methods
    - FTP
    - FTP source
    - Weight
    - Weight source
  contexts:
    web:
      place: web::public::sign-in
- text: The Product signs the person in and takes them where they were going, or Home
  kind: product
  actor: visitor
  entities: []
  contexts:
    web:
      place: web::public::sign-in
references:
- kind: code
  role: implementation
  target: server/internal/auth/callback.go
- kind: code
  role: implementation
  target: server/internal/auth/credentials.go
---

# Sign in for the first time

## Trigger

Someone follows a crew's link or opens WattRoom for the first time.

## Outcome

The person has an account, is signed in, and lands where they were headed; Home asks for their FTP and weight without gating anything.

## Edge cases

- A provider the deployment has not configured is not offered.

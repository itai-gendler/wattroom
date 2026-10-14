---
availability:
- place: web::signed-in
domain: rides
references:
- kind: code
  role: implementation
  target: server/internal/rides/rides.go#handleExport
- kind: code
  role: implementation
  target: server/internal/fitexport/http.go
---

# Download a ride file

A rider downloads one of their rides as a .fit file for another training tool.

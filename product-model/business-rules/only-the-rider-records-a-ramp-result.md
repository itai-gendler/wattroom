---
appliesTo:
- type: entity
  id: ride
  effect: changes
  facts:
  - FTP produced
permits:
- related:
  - verb: owns
    entity: rider
references:
- kind: code
  role: implementation
  target: server/internal/rides/ftp_after.go#handleFtpAfter
---

# Only the rider records the FTP their ramp test produced

The ride keeps the FTP it was scored against; the produced FTP is a mark of its own.

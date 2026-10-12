---
category: security
audience: operators
area: validation
action: none
breaking: false
---

Local test-only validation isolates test code from the host home, temporary files, common service sockets, and external network; dependency roots outside the candidate workspace are rejected and installed dependencies stay read-only. Main image publication and deployment wait for successful hosted validation reconciliation and image scans.

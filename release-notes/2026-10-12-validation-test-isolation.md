---
category: security
audience: operators
area: validation
action: none
breaking: false
---

Local test-only validation now keeps test code away from the host home, temporary files, common service sockets, and external network. Main image publication and deployment wait for successful hosted validation reconciliation and image scans.

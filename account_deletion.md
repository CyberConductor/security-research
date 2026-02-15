## 1. Account Deletion Without Password

**Category:** Broken Authentication  
**Severity:** High  
**Status:** Fixed

### Description
Authenticated users could delete their account without providing a password.  
The server relied solely on session validation and did not require re‑authentication for this destructive action.

### Impact
- Permanent account deletion by anyone with session access  
- Data loss and denial of service for users  
- Exploitable on shared/public devices

### Proof of Concept



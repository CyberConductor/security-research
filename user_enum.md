## 2. User Enumeration via XHR Response

**Category:** Information Disclosure  
**Severity:** Medium  
**Status:** Fixed

### Description
The login endpoint returned different error messages depending on whether a username existed, enabling attackers to enumerate valid accounts.

### Proof of Concept

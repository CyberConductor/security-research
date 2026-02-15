## 2. User Enumeration via XHR Response

**Category:** Information Disclosure  
**Severity:** Medium  
**Status:** Fixed

### Description
The login endpoint returned different error messages depending on whether a username existed, enabling attackers to enumerate valid accounts.

During security testing of a public authentication system, I analysed how the login mechanism handles failed authentication attempts and whether sensitive information leaks through backend responses.

Although the web interface presented a generic error message for invalid credentials, the underlying API responses revealed different behaviours depending on account existence.

### Testing Methodology
Monitored network traffic while interacting with the login form and inspected authentication requests.

### Proof of Concept
**Non-existent user**
POST /api/login
Content-Type: application/json

{
"username": "nonexistent@example.com",
"password": "random"
}


**Response**
{
"__type": "UserNotFoundException",
"message": "User does not exist."
}


**Existing user (wrong password)**
POST /api/login
Content-Type: application/json

{
"username": "validuser@example.com",
"password": "wrongpassword"
}


**Response**
{
"__type": "NotAuthorizedException",
"message": "Incorrect username or password."
}


### Observation
Different backend responses reveal whether an account exists, even though the frontend displays a generic error message.

### Impact
- Account enumeration  
- Targeted phishing attacks  
- Higher success rate for credential stuffing

### Recommendation
Return identical error messages and status codes for all authentication failures and perform authenticat

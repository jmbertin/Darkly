## Location :
Page recover password

## Type of Vulnerability :
Insecure direct objet reference

## Explanation
By inspecting the page, we find a hidden field, which corresponds to the admin's email, we replace it with another one.
-> We get the flag

## Risks
- Identity theft
- Unauthorized access to restricted functions / data
- Cross-site scripting (XSS)
- Privilege escalation

## How to Fix
- Validate session identifiers (tokens, secure cookies)
- Check authorizations
- Obfuscation of references
- Backend validation

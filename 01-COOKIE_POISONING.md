## Location :
Entire site

## Type of Vulnerability :
Cookie poisoning

## Explanation
A cookie is present, the value is in md5 which, once decrypted, gives "false".
We can therefore try to change it to "true" (md5 equivalent: b326b5062b2f0e69046810717534cb09) and refresh the page.
-> We get the flag

## Risks
- Identity theft / session hijacking
- Unauthorized access to restricted functions
- Cross-site scripting (XSS) via cookie

## How to Fix
- Encryption with private key rather than simple hashing
- Backend validation of the cookie's validity and identity
- Use of Secure and HttpOnly Flags, for cookie transmission via HTTPS only
- Limiting cookies in time

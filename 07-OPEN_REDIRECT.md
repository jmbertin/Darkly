## Location :
Entire site

## Type of Vulnerability :
Open redirect (or Unvalidated Redirects and Forwards)

## Explanation
It is possible to take advantage of the redirection to social networks at the bottom of the homepage.
A test with ``http://192.168.41.90/index.php?page=redirect&site=127.0.0.1`` does the trick.
-> We get the flag

## Risks
- Phishing
- Damage to a site's reputation
- Combined with other types of attack (such as XSS)

## How to Fix
- Verify redirects, ensuring that the user is indeed redirected to the desired site
- Whitelist of redirection authorizations
- Use of validation tokens

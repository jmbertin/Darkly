## Location :
Feedback Page

## Type of Vulnerability :
Cross-Site Scripting (XSS)

## Explanation
It is possible to inject code into the page through the form.
The exercise is bugged, it's enough that the word "script" is written in one box or the other and validated.
The page automatically cleans up ``<script>``, ``<body>``, and other tags but not always.
Here is a script that works:
``<svg/onload=alert('XSS')>a``
-> We get the flag

## Risks
- Execution of malicious code
- Identity theft
- Phishing
- Installation of malware
- Damage to the site's reputation
- Unauthorized access to data
- Unauthorized access to restricted functions

## How to Fix
- Escaping user inputs
- Validation of user inputs
- Use of Content Security Policy (CSP), to limit the sources from which scripts can be interpreted / loaded
- Use of libraries and automatic avoidance framework (NodeJS, Django, Express, OWASP Java encoder)

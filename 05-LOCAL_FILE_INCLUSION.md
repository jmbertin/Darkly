## Location :
Entire site

## Type of Vulnerability :
Local file inclusion

## Explanation
On all pages, we notice that it is an inclusion ``index.php?page=XXX``.
It is possible to include whatever we want in the ?page=, so we can try to include the passwd file:
``http://192.168.31.217/index.php?page=../../../../../../../etc/passwd``
-> We get the flag

## Risks
- Exposure of sensitive information
- Execution of malicious code
- Privilege escalation

## How to Fix
- Use of whitelist, allowing only the inclusion of predetermined files
- Limiting privileges to the strict minimum required
- Separation of code and data. Never execute user data (scripts, code...).

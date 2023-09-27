## Location :
Media Page

## Type of Vulnerability :
Cross-Site Scripting (XSS)

## Explanation
When you click on the NSA logo, you are redirected to a page.
By inspecting the homepage, we realize that the href concerning the NSA is not hardcoded but comes from the call to the ``media`` page -> ``/index.php?page=media&src=nsa``
Given that the media page is designed to handle media, we will send it a text media and try to execute JavaScript code:

```
<script>
alert("Hello, World!");
</script>
```
But to pass it to the page we need to ensure that the characters cannot be filtered by the page, so we will encode it in base64: ``/index.php?page=media&src=data:text/html;base64,PHNjcmlwdD4KYWxlcnQoIkhlbGxvLCBXb3JsZCEiKTsKPC9zY3JpcHQ+``
-> We get the flag

## Risks
- Execution of malicious code
- Identity theft
- Phishing
- Installation of malware
- Damage to the site's reputation
- Unauthorized access to data
- Unauthorized access to restricted functions
- Retrieval of the document's cookie like this for example:
``<script>alert(document.cookie);</script>`` -> ``/index.php?page=media&src=data:text/html;base64,PHNjcmlwdD5hbGVydChkb2N1bWVudC5jb29raWUpOzwvc2NyaXB0Pg==``

## How to Fix
- Escaping user inputs
- Validation of user inputs
- Use of Content Security Policy (CSP), to limit the sources * from which scripts can be interpreted / loaded
- Use of libraries and automatic avoidance framework (NodeJS, Django, Express, OWASP Java encoder)

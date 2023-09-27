## Location :
Dans l'arborscence du site

## Type of Vulnerability :
Information disclosure

## Explanation
``http://192.168.31.217/robots.txt`` indicates that two directories should be ignored: whatever and .hidden
In the 'whatever' directory there is a file that contains an htpasswd that contains ``root:437394baff5aa33daa618be47b75cb49``
We decrypt the password and it gives ``qwerty123@``
We try on the members section, without success
After searching the site and many attempts, we find an admin page, ``http://192.168.31.217/admin/``
We try the combination ``root / qwerty123@``
-> We get the flag

## Risks
- Exposure of sensitive data
- Unauthorized access to data
- Unauthorized access to restricted functions
- Identity theft
- Privilege escalation

## How to Fix
- Strict control of file permissions
- Proper management of robots.txt files, which should not be used to try to hide sensitive files / folders
- Encryption of passwords, not just simple hashing
- Configure the server to serve a default page in the absence of an index
- For Apache, for example, a .htaccess file can be placed in the directory to define whether or not the directory tree can be viewed.
- Avoid obvious page or directory names such as "admin"

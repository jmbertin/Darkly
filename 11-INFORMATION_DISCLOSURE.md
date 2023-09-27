## Location :
In the site's tree structure

## Type of Vulnerability :
Information disclosure

## Explanation
``http://192.168.31.217/robots.txt``indicates that two directories should be ignored: whatever and .hidden.
To facilitate searches, we download all the directories / subdirectories / file present in .hidden with the command ``wget -r -e robots=off http://192.168.31.217/.hidden/``
Then, at the root of the directory where we just downloaded the folders, we perform a search with ``grep -r "flag"``.
-> there is also the 'whatever' directory, which contains an htpasswd, with an md5, which, when decrypted, gives qwerty@, it remains to be determined what this password is for.
-> We get the flag

## Risks
- Exposure of sensitive data
- Escalation
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


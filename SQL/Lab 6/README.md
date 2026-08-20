# SQL Injection - Listing Database Contents on Oracle

**Platform:** PortSwigger Web Security Academy  
**Difficulty:** Practitioner  
**Status:** Solved

## Objective

The goal of this lab was to exploit a SQL injection vulnerability in the product category filter and retrieve the usernames and passwords stored in the Oracle database.

The final objective was to obtain the password of the **administrator** user and log in.

## Vulnerability

The application was vulnerable to SQL injection through the `category` parameter. Since the query results were returned in the application's response, a `UNION SELECT` attack could be used to enumerate database tables and retrieve sensitive information.

## Solution

First, I used Burp Suite to intercept and modify the request. I confirmed that the query returned **two columns**, both of which could contain text. Since this was an Oracle database, the `dual` table was required:
```SQL
    ' UNION SELECT 'abc','def' FROM dual--
```
I then enumerated the available tables using Oracle's `all_tables` view:
```SQL
    ' UNION SELECT table_name,NULL FROM all_tables--
```
After identifying the table containing the user credentials, I retrieved its column names using `all_tab_columns`:
```SQL
    ' UNION SELECT column_name,NULL FROM all_tab_columns WHERE table_name='USERS_ABCDEF'--
```
This revealed the columns containing the usernames and passwords.

Finally, I retrieved the stored credentials using:
```SQL
    ' UNION SELECT USERNAME_ABCDEF,PASSWORD_ABCDEF FROM USERS_ABCDEF--
```
The response displayed the usernames and passwords, including the credentials for the **administrator** account. I used the retrieved password to log in as the administrator and complete the lab.

## Key Learning

- `UNION SELECT` can be used to retrieve data from other database tables.
- Oracle provides `all_tables` for enumerating accessible tables.
- `all_tab_columns` can be used to discover the columns within a table.
- Oracle requires a `FROM` clause, so `dual` is useful when no actual table is needed.
- SQL injection can expose sensitive information such as usernames and passwords.

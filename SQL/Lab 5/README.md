# SQL Injection - Listing Database Contents on Non-Oracle Databases

**Platform:** PortSwigger Web Security Academy  
**Difficulty:** Practitioner  
**Status:** Solved

## Objective

The goal of this lab was to exploit a SQL injection vulnerability in the product category filter and retrieve the usernames and passwords stored in the database.

The final objective was to obtain the password of the **administrator** user and log in.

## Vulnerability

The application was vulnerable to SQL injection through the `category` parameter. Since the query results were displayed in the application's response, a `UNION SELECT` attack could be used to enumerate the database and retrieve data from other tables.

## Solution

First, I used Burp Suite to intercept and modify the request. I confirmed that the query returned **two columns**, both of which could contain text:
```SQL
    ' UNION SELECT 'abc','def'--
```
I then enumerated the database tables using:
```SQL
    ' UNION SELECT table_name,NULL FROM information_schema.tables--
```
After identifying the table containing the user credentials, I retrieved its column names using:
```SQL
    ' UNION SELECT column_name,NULL FROM information_schema.columns WHERE table_name='users_abcdef'--
```
This revealed the columns containing the usernames and passwords.

Finally, I retrieved the stored credentials using:
```SQL
    ' UNION SELECT username_abcdef,password_abcdef FROM users_abcdef--
```
The administrator username and password were displayed in the response. I used the retrieved password to log in as the **administrator** user and complete the lab.

## Key Learning

- `UNION SELECT` can be used to retrieve data from other database tables.
- `information_schema.tables` can be used to enumerate database tables.
- `information_schema.columns` can be used to discover table columns.
- SQL injection can expose sensitive information such as usernames and passwords.
- Burp Suite can be used to intercept and modify requests during SQL injection testing.

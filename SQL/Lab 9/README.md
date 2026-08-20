# SQL Injection - UNION Attack: Retrieving Data from Other Tables

**Platform:** PortSwigger Web Security Academy  
**Difficulty:** Practitioner  
**Status:** Solved

## Objective

The goal of this lab was to use a SQL injection `UNION` attack to retrieve usernames and passwords from another table in the database and use the credentials to log in as the **administrator** user.

## Vulnerability

The application was vulnerable to SQL injection through the `category` parameter. Since the query results were returned in the application's response, a `UNION SELECT` attack could be used to retrieve data from the `users` table.

## Solution

First, I used Burp Suite to intercept and modify the request. I determined that the original query returned **two columns**, and both columns were compatible with text data:
```SQL
    ' UNION SELECT 'abc','def'--
```
The database contained a `users` table with `username` and `password` columns. I used the following payload to retrieve the stored credentials:
```SQL
    ' UNION SELECT username,password FROM users--
```
The response displayed the usernames and passwords from the `users` table. I located the credentials for the **administrator** account and used them to log in, completing the lab.

## Key Learning

- `UNION SELECT` can be used to retrieve data from other database tables.
- The number of columns in the injected query must match the original query.
- The data types of the selected columns must be compatible.
- SQL injection can expose sensitive credentials when database queries are not properly protected.

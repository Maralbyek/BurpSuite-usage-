# SQL Injection - UNION Attack: Retrieving Multiple Values in a Single Column

**Platform:** PortSwigger Web Security Academy  
**Difficulty:** Practitioner  
**Status:** Solved

## Objective

The goal of this lab was to use a SQL injection `UNION` attack to retrieve multiple values from the `users` table when only **one column was compatible with text data**.

The final objective was to retrieve the usernames and passwords and use the credentials to log in as the **administrator** user.

## Vulnerability

The application was vulnerable to SQL injection through the `category` parameter. The query returned two columns, but only one of them was compatible with text data.

## Solution

First, I used Burp Suite to intercept and modify the request. I confirmed that the query returned **two columns**, with only the second column accepting text:

    ' UNION SELECT NULL,'abc'--

Since only one column could display text, I combined the `username` and `password` values into a single column using the `||` concatenation operator:

    ' UNION SELECT NULL,username||'~'||password FROM users--

The `~` character was used as a separator between the username and password, making the retrieved values easier to identify in the response.

The response displayed the usernames and passwords from the `users` table in a single column. I located the credentials for the **administrator** account and used them to log in, completing the lab.

## Key Learning

- A `UNION SELECT` attack requires the same number of columns as the original query.
- When only one column can display text, multiple values can be combined into that column.
- The `||` operator can be used to concatenate strings in SQL.
- A separator can make multiple concatenated values easier to read.
- SQL injection can expose sensitive credentials when user input is directly included in database queries.

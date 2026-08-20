# SQL Injection - UNION Attack: Determining the Number of Columns

**Platform:** PortSwigger Web Security Academy  
**Difficulty:** Practitioner  
**Status:** Solved

## Objective

The goal of this lab was to determine the **number of columns returned by the original SQL query** using a SQL injection `UNION` attack.

This is an important first step when performing a UNION-based SQL injection because the injected query must return the same number of columns as the original query.

## Vulnerability

The application was vulnerable to SQL injection through the `category` parameter. Since the query results were returned in the application's response, I could use ```SQL UNION SELECT ``` to test how many columns the original query contained.

## Solution

I used Burp Suite to intercept and modify the request containing the `category` parameter.

I first tested a single column:
```SQL
    ' UNION SELECT NULL--
```
This produced an error, meaning the number of columns did not match.

I then added another `NULL` value:
```SQL
    ' UNION SELECT NULL,NULL--
```
The response no longer produced an error, confirming that the original query returned **two columns**.

## Key Learning

- A `UNION` query must return the same number of columns as the original query.
- `NULL` values are useful for determining the number of columns without worrying about data types.
- Burp Suite can be used to modify parameters and observe how the application responds to different SQL injection payloads.
- Determining the column count is an important first step in a UNION-based SQL injection attack.

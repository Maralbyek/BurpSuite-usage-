# SQL Injection - Querying the Database Version on MySQL and Microsoft

**Platform:** PortSwigger Web Security Academy  
**Difficulty:** Practitioner  
**Status:** Solved

## Objective

The goal of this lab was to exploit a SQL injection vulnerability in the product category filter and retrieve the **database version**.

## Vulnerability

The application was vulnerable to SQL injection through the `category` parameter. A `UNION SELECT` attack could be used to inject a query and retrieve information from the database.

## Solution

First, I used Burp Suite to intercept and modify the request containing the product category.

I determined that the original query returned **two columns**, and both columns could contain text. I tested this with:

```sql
' UNION SELECT 'abc','def'#

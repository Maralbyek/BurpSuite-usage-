# SQL Injection - Retrieving Hidden Data

**Platform:** PortSwigger Web Security Academy  
**Difficulty:** Apprentice  
**Status:** Solved

## Objective

The goal of this lab was to exploit a SQL injection vulnerability in the product category filter and retrieve products that were marked as unreleased.

## Vulnerability

The application uses the selected category directly in a SQL query:

```sql
SELECT * FROM products WHERE category = 'Gifts' AND released = 1

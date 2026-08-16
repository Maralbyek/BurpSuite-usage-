# SQL Injection - Login Bypass

**Platform:** PortSwigger Web Security Academy  
**Difficulty:** Apprentice  
**Status:** Solved

## Objective

The goal of this lab was to exploit a SQL injection vulnerability in the login function and bypass the authentication process to log in as the `administrator` user.

## Vulnerability

The login function was vulnerable to SQL injection because the username input could be manipulated to alter the underlying SQL query.

## Exploitation

I modified the `username` parameter with the following payload:

```text
administrator'--

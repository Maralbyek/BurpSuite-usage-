# SQL Injection - UNION Attack: Finding a Column Containing Text

**Platform:** PortSwigger Web Security Academy  
**Difficulty:** Practitioner  
**Status:** Solved

## Objective

The goal of this lab was to identify which column in the SQL query was compatible with **text data** using a SQL injection `UNION` attack.

The lab provided a random value that had to be successfully displayed in the application's response.

## Vulnerability

The application was vulnerable to SQL injection through the `category` parameter. Since the query results were returned in the application's response, I could use a `UNION SELECT` attack to test the data type accepted by each column.

## Solution

First, I determined that the original query returned **three columns** by using:

    ' UNION SELECT NULL,NULL,NULL--

I then replaced each `NULL` value one at a time with the random string provided by the lab:

    ' UNION SELECT 'abcdef',NULL,NULL--

If an error occurred, I moved the string to the next column:

    ' UNION SELECT NULL,'abcdef',NULL--

Then:

    ' UNION SELECT NULL,NULL,'abcdef'--

When the random value appeared successfully in the response, I identified the column that was compatible with **text data**.

## Key Learning

- The number of columns in a `UNION SELECT` must match the original query.
- `NULL` values can be used to test different columns without initially worrying about data types.
- Testing each column with a string helps identify which columns accept text data.
- Finding a text-compatible column is an important step before retrieving string-based data through UNION SQL injection.

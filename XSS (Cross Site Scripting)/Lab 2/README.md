# Stored XSS Lab

This project documents a PortSwigger Web Security Academy lab demonstrating a basic Stored Cross-Site Scripting (XSS) vulnerability in an HTML context where user input is not encoded.

## Lab Information

- **Vulnerability:** Stored Cross-Site Scripting (XSS)
- **Context:** HTML
- **Difficulty:** Apprentice
- **Status:** Solved
- **Target Function:** Comment functionality

## Solution

1. Enter the following XSS payload into the comment box:
   `<script>alert(1)</script>`
2. Enter a valid name, email, and website if required.
3. Click **Post comment**.
4. Return to the blog post where the comment was submitted.
5. The stored payload is loaded with the page and executed by the browser.
6. The `alert(1)` function is triggered when the stored comment is displayed.

## Payload Used

```html
<script>alert(1)</script>

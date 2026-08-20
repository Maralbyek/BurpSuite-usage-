# Reflected XSS Lab

This project documents a PortSwigger Web Security Academy lab demonstrating a basic Reflected Cross-Site Scripting (XSS) vulnerability in an HTML context where user input is not encoded.

## Lab Information

- **Vulnerability:** Reflected Cross-Site Scripting (XSS)
- **Context:** HTML
- **Difficulty:** Apprentice
- **Status:** Solved
- **Target Function:** Search functionality

## Solution

1. Enter the following XSS payload into the search box:
   `<script>alert(1)</script>`
2. Click **Search**.
3. The input is reflected directly into the HTML page without encoding.
4. The browser interprets the injected `<script>` element and executes `alert(1)`.

## Payload Used

```html
<script>alert(1)</script>

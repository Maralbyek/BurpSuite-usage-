# Stored XSS Lab

This project documents a PortSwigger Web Security Academy lab demonstrating a basic Stored Cross-Site Scripting (XSS) vulnerability in an HTML context where user input is not encoded.

## Lab Information

- **Vulnerability:** Stored Cross-Site Scripting (XSS)
- **Context:** HTML
- **Difficulty:** Apprentice
- **Status:** Solved
- **Target Function:** Comment functionality

## Payload Used

```html
<script>alert(1)</script>

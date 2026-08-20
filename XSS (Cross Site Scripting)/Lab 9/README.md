# Reflected XSS into a JavaScript String with Angle Brackets HTML-Encoded

This project documents a PortSwigger Web Security Academy lab demonstrating a reflected Cross-Site Scripting (XSS) vulnerability where user-controlled input is reflected inside a JavaScript string. Angle brackets are HTML-encoded, but the JavaScript string can still be escaped.

## Lab Information

- **Vulnerability:** Reflected Cross-Site Scripting (XSS)
- **Context:** JavaScript string
- **Difficulty:** Apprentice
- **Status:** Solved
- **Encoding:** Angle brackets HTML-encoded

## Payload Used

```javascript
'-alert(1)-'

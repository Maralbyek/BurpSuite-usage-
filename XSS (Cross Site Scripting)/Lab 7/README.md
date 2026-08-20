# Reflected XSS into Attribute with Angle Brackets HTML-Encoded

This project documents a PortSwigger Web Security Academy lab demonstrating a reflected Cross-Site Scripting (XSS) vulnerability where angle brackets are HTML-encoded, but an attacker can still escape a quoted HTML attribute and inject an event handler.

## Lab Information

- **Vulnerability:** Reflected Cross-Site Scripting (XSS)
- **Context:** HTML attribute
- **Difficulty:** Apprentice
- **Status:** Solved
- **Encoding:** Angle brackets HTML-encoded

## Payload Used

```html
"onmouseover="alert(1)

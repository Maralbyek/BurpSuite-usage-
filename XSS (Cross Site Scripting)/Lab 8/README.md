# Stored XSS into Anchor href Attribute with Double Quotes HTML-Encoded

This project documents a PortSwigger Web Security Academy lab demonstrating a stored Cross-Site Scripting (XSS) vulnerability where user-controlled input is stored in a comment and reflected inside an anchor `href` attribute.

## Lab Information

- **Vulnerability:** Stored Cross-Site Scripting (XSS)
- **Context:** HTML `href` attribute
- **Difficulty:** Apprentice
- **Status:** Solved
- **Encoding:** Double quotes HTML-encoded

## Payload Used

```javascript
javascript:alert(1)

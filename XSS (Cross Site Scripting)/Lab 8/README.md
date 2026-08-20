# Stored XSS into Anchor href Attribute with Double Quotes HTML-Encoded

This project documents a PortSwigger Web Security Academy lab demonstrating a stored Cross-Site Scripting (XSS) vulnerability where user-controlled input is stored in a comment and reflected inside an anchor `href` attribute.

## Lab Information

- **Vulnerability:** Stored Cross-Site Scripting (XSS)
- **Context:** HTML `href` attribute
- **Difficulty:** Apprentice
- **Status:** Solved
- **Encoding:** Double quotes HTML-encoded

## Solution

1. Post a comment with a random value in the **Website** field.
2. Use Burp Suite to inspect how the value is stored and reflected.
3. Observe that the value is placed inside the comment author's `href` attribute.
4. Replace the Website value with the payload below.
5. View the comment and click the author's name to trigger the alert.

## Payload Used

```javascript
javascript:alert(1)

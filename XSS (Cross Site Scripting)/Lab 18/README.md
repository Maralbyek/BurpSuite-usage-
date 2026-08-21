# Reflected XSS into JavaScript String with Single Quote and Backslash Escaped Lab

This project documents a PortSwigger Web Security Academy lab demonstrating a reflected Cross-Site Scripting (XSS) vulnerability where user-controlled input is reflected inside a JavaScript string. Single quotes and backslashes are escaped, preventing a direct escape from the JavaScript string.

## Lab Information

- **Vulnerability:** Reflected Cross-Site Scripting (XSS)
- **Context:** JavaScript string
- **Difficulty:** Practitioner
- **Status:** Solved
- **Encoding:** Single quotes and backslashes escaped
- **Target Function:** Search query tracking

## Solution

1. Submit a random alphanumeric string in the search box.
2. Use Burp Suite to intercept the search request and send it to Burp Repeater.
3. Observe that the input is reflected inside a JavaScript string.
4. Test the following input:

```javascript
test'payload

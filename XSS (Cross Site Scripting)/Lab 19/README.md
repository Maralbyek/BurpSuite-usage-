# Reflected XSS into JavaScript String with Angle Brackets and Double Quotes HTML-Encoded and Single Quotes Escaped Lab

This project documents a PortSwigger Web Security Academy lab demonstrating a reflected Cross-Site Scripting (XSS) vulnerability where user-controlled input is reflected inside a JavaScript string. Angle brackets and double quotes are HTML-encoded, while single quotes are escaped.

## Lab Information

- **Vulnerability:** Reflected Cross-Site Scripting (XSS)
- **Context:** JavaScript string
- **Difficulty:** Practitioner
- **Status:** Solved
- **Encoding:** Angle brackets and double quotes HTML-encoded; single quotes escaped
- **Target Function:** Search query tracking

## Solution

1. Submit a random alphanumeric string in the search box.
2. Use Burp Suite to intercept the search request and send it to Burp Repeater.
3. Observe that the random string is reflected inside a JavaScript string.
4. Test the following payload:

```javascript
test\payload
```
and
```javascript
\'-alert(1)//
```

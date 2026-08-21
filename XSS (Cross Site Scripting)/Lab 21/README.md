# Reflected XSS into a Template Literal Lab

This project documents a PortSwigger Web Security Academy lab demonstrating a reflected Cross-Site Scripting (XSS) vulnerability where user-controlled input is reflected inside a JavaScript template literal. Angle brackets, single quotes, and double quotes are HTML-encoded, while backticks are escaped.

## Lab Information

- **Vulnerability:** Reflected Cross-Site Scripting (XSS)
- **Context:** JavaScript template literal
- **Difficulty:** Practitioner
- **Status:** Solved
- **Encoding:** Angle brackets, single quotes, and double quotes HTML-encoded; backticks escaped
- **Target Function:** Search functionality

## Solution

1. Submit a random alphanumeric string in the search box.
2. Use Burp Suite to intercept the search request and send it to Burp Repeater.
3. Observe that the input is reflected inside a JavaScript template literal.
4. Since the input is already inside a template literal, use JavaScript template literal expression syntax to execute code.
5. Enter the following payload:

```javascript
${alert(1)}

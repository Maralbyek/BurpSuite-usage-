# Reflected XSS into Attribute with Angle Brackets HTML-Encoded

This project documents a PortSwigger Web Security Academy lab demonstrating a reflected Cross-Site Scripting (XSS) vulnerability where angle brackets are HTML-encoded, but an attacker can still escape a quoted HTML attribute and inject an event handler.

## Lab Information

- **Vulnerability:** Reflected Cross-Site Scripting (XSS)
- **Context:** HTML attribute
- **Difficulty:** Apprentice
- **Status:** Solved
- **Encoding:** Angle brackets HTML-encoded

## Solution

1. Submit a random alphanumeric string in the search box.
2. Use Burp Suite to inspect the request and response.
3. Observe that the input is reflected inside a quoted HTML attribute.
4. Replace the input with the payload below to escape the existing attribute and inject an event handler.
5. Open the resulting URL and move the mouse over the affected element to trigger the alert.

## Payload Used

```html
"onmouseover="alert(1)

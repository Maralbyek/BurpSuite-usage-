# Reflected XSS with Some SVG Markup Allowed Lab

This project documents a PortSwigger Web Security Academy lab demonstrating a reflected Cross-Site Scripting (XSS) vulnerability where common HTML tags are blocked, but certain SVG elements and event handlers are allowed.

## Lab Information

- **Vulnerability:** Reflected Cross-Site Scripting (XSS)
- **Context:** HTML / SVG
- **Difficulty:** Practitioner
- **Status:** Solved
- **Target Function:** Search functionality
- **Protection:** Common HTML tags and events blocked

## Solution

1. Test a standard XSS payload and observe that it is blocked.
2. Use Burp Intruder to identify which HTML/SVG tags are allowed.
3. Testing shows that `<svg>`, `<animatetransform>`, `<title>`, and `<image>` receive a `200` response.
4. Use `<svg>` with `<animatetransform>` and test different event handlers.
5. Burp Intruder identifies `onbegin` as an allowed event handler.
6. Combine the allowed SVG tag and event handler to create the XSS payload.
7. Visit the resulting URL to trigger `alert(1)` and solve the lab.

## Payload Used

```html
<svg><animatetransform onbegin=alert(1)>

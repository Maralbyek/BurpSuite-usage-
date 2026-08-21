# Reflected XSS with Most Tags and Attributes Blocked Lab

This project documents a PortSwigger Web Security Academy lab demonstrating a reflected Cross-Site Scripting (XSS) vulnerability protected by a Web Application Firewall (WAF) that blocks most common HTML tags and event-handler attributes.

## Lab Information

- **Vulnerability:** Reflected Cross-Site Scripting (XSS)
- **Context:** HTML
- **Difficulty:** Practitioner
- **Status:** Solved
- **Target Function:** Search functionality
- **Protection:** Web Application Firewall (WAF)
- **Target Function:** `print()`

## Solution

1. Test a standard XSS payload and observe that it is blocked by the WAF.
2. Use Burp Intruder to test which HTML tags are allowed.
3. The `body` tag returns a `200` response while most other tags return `400`.
4. Test event-handler attributes against the `body` tag.
5. The `onresize` attribute returns a `200` response.
6. Combine the allowed tag and attribute to create the XSS payload.
7. Use the exploit server to deliver the payload to the victim without requiring user interaction.

## Payload Used

```html
<body onresize=print()>

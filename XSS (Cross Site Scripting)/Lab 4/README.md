# DOM XSS in innerHTML Lab

This project documents a PortSwigger Web Security Academy lab demonstrating a DOM-based Cross-Site Scripting (XSS) vulnerability caused by an `innerHTML` assignment using user-controlled data from `location.search`.

## Lab Information

- **Vulnerability:** DOM-based Cross-Site Scripting (XSS)
- **Sink:** `innerHTML`
- **Source:** `location.search`
- **Difficulty:** Apprentice
- **Status:** Solved
- **Target Function:** Search functionality

## Payload Used

```html
<img src=1 onerror=alert(1)>

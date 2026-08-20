# DOM XSS in document.write Lab

This project documents a PortSwigger Web Security Academy lab demonstrating a DOM-based Cross-Site Scripting (XSS) vulnerability caused by the use of `document.write` with user-controlled data from `location.search`.

## Lab Information

- **Vulnerability:** DOM-based Cross-Site Scripting (XSS)
- **Sink:** `document.write`
- **Source:** `location.search`
- **Difficulty:** Apprentice
- **Status:** Solved
- **Target Function:** Search query tracking

## Solution

1. Enter a random alphanumeric string into the search box.
2. Inspect the page and observe that the search input is inserted inside an `img src` attribute.
3. Replace the search input with the following payload:
   `"><svg onload=alert(1)>`
4. Submit the search query.
5. The payload breaks out of the existing `img` attribute and injects an SVG element.
6. The `onload` event executes `alert(1)`.

## Payload Used

```html
"><svg onload=alert(1)>

# DOM XSS in innerHTML Lab

This project documents a PortSwigger Web Security Academy lab demonstrating a DOM-based Cross-Site Scripting (XSS) vulnerability caused by an `innerHTML` assignment using user-controlled data from `location.search`.

## Lab Information

- **Vulnerability:** DOM-based Cross-Site Scripting (XSS)
- **Sink:** `innerHTML`
- **Source:** `location.search`
- **Difficulty:** Apprentice
- **Status:** Solved
- **Target Function:** Search functionality

## Solution

1. Enter the following payload into the search box:
   `<img src=1 onerror=alert(1)>`
2. Click **Search**.
3. The search input is inserted into the page using the `innerHTML` sink.
4. The invalid image source causes an error.
5. The `onerror` event handler executes `alert(1)`.

## Payload Used

```html
<img src=1 onerror=alert(1)>

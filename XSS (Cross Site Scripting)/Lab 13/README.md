# Stored DOM XSS Lab

This project documents a PortSwigger Web Security Academy lab demonstrating a Stored DOM-based Cross-Site Scripting (XSS) vulnerability in the blog comment functionality.

## Lab Information

- **Vulnerability:** Stored DOM-based Cross-Site Scripting (XSS)
- **Context:** Blog comments
- **Difficulty:** Practitioner
- **Status:** Solved
- **Target Function:** Comment functionality
- **Filter:** JavaScript `replace()` function

## Solution

1. Post a comment containing the following payload.
2. The application attempts to prevent XSS by using JavaScript `replace()` to encode angle brackets.
3. The filter only replaces the first occurrence because the first argument is a string rather than a global regular expression.
4. The first pair of angle brackets is therefore encoded, while the second pair remains unchanged.
5. The remaining HTML is interpreted by the browser, causing the `onerror` event to execute `alert(1)`.

## Payload Used

```html
<><img src=1 onerror=alert(1)>

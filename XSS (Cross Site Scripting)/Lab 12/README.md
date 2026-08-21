# Reflected DOM XSS Lab

This project documents a PortSwigger Web Security Academy lab demonstrating a Reflected DOM-based Cross-Site Scripting (XSS) vulnerability where reflected data is processed unsafely by client-side JavaScript.

## Lab Information

- **Vulnerability:** Reflected DOM-based Cross-Site Scripting (XSS)
- **Context:** JSON response processed by JavaScript
- **Difficulty:** Practitioner
- **Status:** Solved
- **Source:** Reflected search input
- **Sink:** `eval()`
- **Target Function:** Search functionality

## Solution

1. Enable **Intercept** in Burp Suite Proxy.
2. Use the search bar to submit a random test string such as `"XSS"`.
3. Forward the request through Burp Suite.
4. Observe that the search string is reflected inside the `search-results` JSON response.
5. Inspect `searchResults.js` and identify that the JSON response is processed using `eval()`.
6. Test different inputs and observe that quotation marks are escaped, but backslashes are not properly escaped.
7. Use the following payload in the search functionality:

```javascript
\"-alert(1)}//

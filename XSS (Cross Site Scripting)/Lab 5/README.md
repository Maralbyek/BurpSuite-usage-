# DOM XSS in jQuery href Attribute Lab

This project documents a PortSwigger Web Security Academy lab demonstrating a DOM-based Cross-Site Scripting (XSS) vulnerability caused by a jQuery `href` attribute modification using user-controlled data from `location.search`.

## Lab Information

- **Vulnerability:** DOM-based Cross-Site Scripting (XSS)
- **Sink:** jQuery `href` attribute
- **Source:** `location.search`
- **Difficulty:** Apprentice
- **Status:** Solved
- **Target Function:** Submit feedback page / Back link

## Solution

1. Open the **Submit feedback** page.
2. Change the `returnPath` query parameter to `/` followed by a random alphanumeric string.
3. Inspect the **Back** link and observe that the value is inserted into its `href` attribute.
4. Change the `returnPath` parameter to:
   `javascript:alert(document.cookie)`
5. Load the modified URL.
6. Click the **Back** link.
7. The JavaScript URL executes and displays the value of `document.cookie`.

## Payload Used

```javascript
javascript:alert(document.cookie)

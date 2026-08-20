# DOM XSS in document.write Sink Using location.search Inside a Select Element

This project documents a PortSwigger Web Security Academy lab demonstrating a DOM-based Cross-Site Scripting (XSS) vulnerability where user-controlled data from `location.search` is passed to `document.write` inside a `<select>` element.

## Lab Information

- **Vulnerability:** DOM-based Cross-Site Scripting (XSS)
- **Context:** HTML `<select>` element
- **Sink:** `document.write`
- **Source:** `location.search`
- **Difficulty:** Practitioner
- **Status:** Solved
- **Target Function:** Stock checker

## Solution

1. Open a product page and identify that the `storeId` parameter is taken from `location.search`.
2. Add a `storeId` parameter with a random alphanumeric value to the URL.
3. Load the modified URL and observe that the value appears as an option in the stock checker drop-down.
4. Inspect the drop-down element and confirm that the `storeId` value is inserted inside the `<select>` element.
5. Replace the `storeId` value with the following payload:

```html
"></select><img src=1 onerror=alert(1)>

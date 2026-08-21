# DOM XSS in AngularJS Expression Lab

This project documents a PortSwigger Web Security Academy lab demonstrating a DOM-based Cross-Site Scripting (XSS) vulnerability involving an AngularJS expression in the search functionality.

## Lab Information

- **Vulnerability:** DOM-based Cross-Site Scripting (XSS)
- **Context:** AngularJS expression
- **Difficulty:** Practitioner
- **Status:** Solved
- **Target Function:** Search functionality
- **Encoding:** Angle brackets and double quotes HTML-encoded

## Solution

1. Enter a random alphanumeric string into the search box.
2. View the page source and observe that the search input is enclosed within an `ng-app` directive.
3. Enter the following AngularJS expression into the search box:
4. Click **Search**.
5. The AngularJS expression is evaluated and executes the `alert(1)` function.

## Payload Used

```javascript
{{$on.constructor('alert(1)')()}}

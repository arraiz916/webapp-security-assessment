# 04 — Missing Content-Security-Policy

|            |                                                     |
|------------|-----------------------------------------------------|
| Severity   | **Medium**                                          |
| Category   | OWASP A05:2021 — Security Misconfiguration          |
| CWE        | CWE-693: Protection Mechanism Failure               |
| Status     | Open                                                |

## Summary

No `Content-Security-Policy` header is present on any application response.

## Impact

CSP is a key defense-in-depth control against cross-site scripting and injection. Its absence
is especially significant here because the session token is stored in script-readable
`localStorage` ([Finding 01](./01-session-token-localstorage.md)): a CSP restricting script
sources would meaningfully reduce the exploitability of any XSS flaw against that token.

## Steps to reproduce

1. Load an authenticated page.
2. DevTools → **Network** → select the main document request → **Response Headers**.
3. Confirm no `Content-Security-Policy` header is returned on any response.

## Evidence

Reproducible directly via the steps above: DevTools → Network → main document →
Response Headers shows no `Content-Security-Policy` entry on any response.

## Remediation

- Deploy a restrictive CSP: default-deny, explicit allow-lists for script / style / connect
  sources, and `frame-ancestors 'self'` (which also covers
  [Finding 03](./03-missing-clickjacking-protection.md)).
- Roll out in `Content-Security-Policy-Report-Only` mode first to tune without breaking
  functionality, then move to enforcement.

## References

- OWASP Top 10 2021 — A05: Security Misconfiguration
- OWASP Secure Headers Project
- CWE-693: Protection Mechanism Failure

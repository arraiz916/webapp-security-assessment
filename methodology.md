# Methodology

## Approach

Manual, evidence-driven security testing focused on authentication, session management,
authorization, security headers, and input handling. Each test was executed as a formal case:
preconditions, test data, steps, expected result, actual result, status, and a qualitative
severity rating, with screenshot evidence.

## Tools

- **Browser DevTools** (Chrome) — Storage, Network, and Console panels for inspecting tokens,
  headers, and responses.
- **Burp Suite** — intercepting proxy for tampering with multipart upload requests.
- **JWT decoding** — base64url decode of header/payload to inspect `alg` and `exp`.
- **Custom PoC HTML** — local iframe page to demonstrate framing / clickjacking.

## Severity scale

| Rating        | Meaning                                                     |
|---------------|-------------------------------------------------------------|
| Critical      | Direct, unauthenticated compromise                          |
| High          | Serious impact, or serious when chained with a plausible flaw |
| Medium        | Meaningful weakness / missing defense-in-depth              |
| Low           | Minor or cosmetic                                           |
| Informational | Verified-secure control or methodology note                 |

## Reporting

Findings mapped to OWASP Top 10 (2021) and CWE, each with concrete remediation. Passing
controls are documented alongside failures for completeness.

# Web Application Security Assessment — Session, Authentication & Authorization Controls

A sanitized security assessment of a compliance / audit-readiness web application,
performed as the dedicated **security tester** on a five-person Agile QA team over two sprints.

> **Context & sanitization.** Conducted as authorized testing for a university
> software-quality course (CSC 179, California State University, Sacramento — Summer 2026)
> against a live client application provided through the course. All client-identifying
> details — company name, hostname, storage-key names, and account data — have been
> **redacted**, and findings are presented as sanitized case studies for portfolio
> purposes. This write-up neither identifies the client nor functions as an exploit
> guide against any live system.

**Role:** Security tester — authentication, session management, authorization, security headers, input validation.

**Independent evaluation:** In the sprint reviews, the security testing scored **5/5** on
Test Effectiveness, Completeness, and Usefulness (95/100 overall in Sprint 2) and was noted
by the reviewing instructor as *"unique compared to many other teams."* (Team-level score;
security was my area of ownership.)

---

## Scope

- Session / authentication token storage and client-side exposure
- Server-side authorization and resistance to privilege escalation
- Session lifecycle — logout and server-side token invalidation
- JWT signing algorithm and expiry
- Security response headers (anti-framing, Content-Security-Policy)
- Stored XSS via file-upload metadata

## Methodology

Manual, evidence-driven testing. Each test was recorded as a formal case (preconditions,
steps, expected vs. actual result, status, severity) with screenshot evidence. See
[`methodology.md`](./methodology.md).

Tooling: browser DevTools (Storage / Network / Console), Burp Suite (request interception
and multipart tampering), JWT decoding, and custom proof-of-concept HTML.

## Findings

| #  | Finding | Severity | OWASP 2021 | CWE | Status |
|----|---------|----------|------------|-----|--------|
| 01 | [Session token stored in browser localStorage](./findings/01-session-token-localstorage.md) | High* | A07 | CWE-522 | Open |
| 02 | [Session token not invalidated on logout (replayable)](./findings/02-token-replay-after-logout.md) | High | A07 | CWE-613 | Open |
| 03 | [Missing clickjacking protection](./findings/03-missing-clickjacking-protection.md) | High | A05 | CWE-1021 | Open |
| 04 | [Missing Content-Security-Policy](./findings/04-missing-content-security-policy.md) | Medium | A05 | CWE-693 | Open |
| 05 | [Verified controls (access control, JWT, XSS)](./findings/05-verified-controls.md) | Info | A01 / A03 | — | Passed |

*High when chained with any XSS flaw; Medium in isolation.

Redacted evidence lives in [`/evidence`](./evidence).

## Responsible disclosure

Findings were reported to the client through the course's supervising instructor. This
public version is sanitized so that it cannot be used to identify or attack any live system.

## Tools

Burp Suite · Chrome DevTools · JWT decoding · custom PoC HTML

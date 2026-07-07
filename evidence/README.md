# Evidence

Redacted screenshots supporting the findings. Filenames referenced by the write-ups:

| File | Supports |
|------|----------|
| `01-localstorage-token.png` | Finding 01 — token in localStorage |
| `02-token-replay.png` | Finding 02 — token replay after logout |
| `03-clickjacking-poc.png` | Finding 03 — clickjacking PoC |
| `05-role-tamper-403.png` | Finding 05.1 — role tamper → 403 |
| `05-cached-304-network.png` | Finding 05.2 — cached 304 false-positive |
| `05-jwt-decode.png` | Finding 05.3 — JWT header/expiry |

## Redaction applied to every image

- JWT / token values
- Client / company / product name and logo
- Hostnames and URLs (address bar, DevTools origin labels, Network domain column)
- Account emails and any personal browser chrome (tabs, bookmarks, OS username in file paths)

All redaction is solid-box or crop on flattened PNGs — no blur on text.

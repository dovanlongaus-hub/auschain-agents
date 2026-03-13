# Skill: OWASP Web Security 2025/2026
**Version:** 1.0 | **Date:** 2026-03-13 | **Agent:** Shield 🛡️

## OWASP Top 10 Web 2025 — Key Changes from 2021

> ⚠️ OWASP published updated Top 10 for Web Applications in 2025 (first update since 2021).  
> Category numbering and names have changed — update any internal checklists.

### Top 10 (2025 edition — new mapping)
| # | Category | Key concern |
|---|----------|-------------|
| A01 | Broken Access Control | Still #1; IDOR, path traversal, privilege escalation |
| A02 | Cryptographic Failures | Weak algorithms, TLS misconfig, key exposure |
| A03 | Injection | SQL, NoSQL, LDAP, command injection |
| A04 | **Insecure Design** _(new 2025)_ | Missing threat models, insecure architecture patterns |
| A05 | Security Misconfiguration | Default creds, permissive CORS, verbose errors, open cloud buckets |
| A06 | Vulnerable & Outdated Components | Unpatched deps, end-of-life libraries |
| A07 | Identification & Authentication Failures | Weak sessions, credential stuffing |
| A08 | **Software & Data Integrity Failures** _(new 2025)_ | CI/CD poisoning, unsigned updates, insecure deserialization |
| A09 | Security Logging & Monitoring Failures | Missing audit logs, no alerting |
| A10 | **Server-Side Request Forgery (SSRF)** _(new 2025)_ | Cloud metadata endpoint abuse, internal network access |

### Critical for Auschain (migration/visa SaaS)
- **A01 Broken Access Control**: Ensure multi-tenant isolation — users must NEVER see other companies' migration cases
- **A05 Misconfiguration**: Audit CORS policy — overly permissive CORS is a top exploit vector
- **A08 Software & Data Integrity**: Sign all deployment artifacts; verify supply chain (npm audit)
- **A10 SSRF**: Any user-supplied URL input (file upload, webhooks) must be validated against internal IP ranges

### OWASP LLM Top 10 (if AI features used)
- **LLM01 Prompt Injection** — ranked #1, no foolproof prevention; use output validation + sandboxing
- Sanitize all AI-generated content before rendering in UI

### Quick wins for Node.js backend
```javascript
// Prevent common misconfigs
app.disable('x-powered-by');  // don't leak Express version
app.use(helmet());             // security headers (CSP, HSTS, etc.)

// CORS — be explicit, not permissive
app.use(cors({
  origin: ['https://auschain.com.au', 'https://app.auschain.com.au'],
  credentials: true,
}));

// SSRF protection for any URL fetch
import { isPrivateIP } from './utils/network';
async function safeFetch(url) {
  const { hostname } = new URL(url);
  if (isPrivateIP(hostname)) throw new Error('SSRF blocked');
  return fetch(url);
}
```

## Changelog
- v1.0: Initial — OWASP Web 2025 update, LLM risks, Node.js mitigations

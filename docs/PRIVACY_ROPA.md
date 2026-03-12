# Record of Processing Activities (Minimal - SmallQR)

| Item | Description |
|------|-------------|
| Controller | Francesco Vigni |
| Purpose | Provide on-demand QR code generation for user-supplied text/links |
| Data Categories | Transient input text (could contain personal data), session captcha answer (ephemeral), IP & user-agent (logs), aggregate counter (non-personal) |
| Legal Basis | Legitimate Interest (Article 6(1)(f)) – providing requested functional service with minimal data |
| Recipients / Processors | Cloudflare (reverse proxy, security), Hosting provider (runtime), CDN (Bootstrap/JS – until self-host), Coveralls badge (image fetch) |
| International Transfers | Possible via Cloudflare; safeguarded by SCCs (see Cloudflare DPA) |
| Retention | Input text not stored; session ephemeral; logs (IP, UA) up to 30 days; aggregate counter persisted as numeric total only |
| Security Measures | HTTPS, no database storage of input, security headers (CSP, Referrer-Policy, etc.), rate limiting, minimal dependencies |
| Special Categories | Not targeted / not intentionally processed |
| Automated Decision / Profiling | None |
| Data Subject Rights Handling | Best-effort explanation—no stored user content to retrieve or erase post-response |
| DPIA | Not required (low risk, minimal scope, no systematic monitoring) |

# Security Policy

## Supported Versions

StackEdit++ is an in-browser web application running directly in browser process memory at [https://stackeditplusplus.meshworld.in](https://stackeditplusplus.meshworld.in) (with the app interface at [https://stackeditplusplus.meshworld.in/app](https://stackeditplusplus.meshworld.in/app)). All web users access the latest deployed build automatically.

| Version / Deployment | Supported          |
| -------------------- | ------------------ |
| Web Production       | :white_check_mark: |
| Self-hosted / Forks  | :x:                |

---

## Security Model & Threat Vectors

Because StackEdit++ executes 100% client-side in browser memory with zero server telemetry for user documents, security considerations specifically focus on:
- **Cross-Site Scripting (XSS)** vectors within Markdown AST compilation, HTML sanitization, or preview extensions (KaTeX, Mermaid, ABCjs, Prism code highlighters).
- **Client-Side Storage Isolation**: Proper sandbox segregation of IndexedDB and localStorage keys.
- **Unintended External Network Requests**: Preventing preview engines from initiating unauthorized remote requests or exfiltrating user keystrokes.
- **Content-Security-Policy (CSP)** adherence and strict frame origin controls.

---

## Reporting a Vulnerability

The StackEdit++ engineering team takes document privacy and client-side isolation seriously.

### Disclosure Protocol

1. **Do NOT open a public GitHub issue** for undisclosed security vulnerabilities.
2. Submit a private report via **[GitHub Private Vulnerability Reporting](https://github.com/cooldashing24/stackedit-community/security/advisories/new)** with:
   - Specific component or URL where the issue was observed.
   - Detailed step-by-step reproduction instructions or a minimal proof-of-concept (PoC) Markdown document.
   - Impact assessment (e.g., DOM XSS, storage leak, CSP bypass).
3. You will receive an acknowledgment within **48 hours**.
4. We coordinate rapid patch deployment directly to production and credit researchers in our release notes upon verification.

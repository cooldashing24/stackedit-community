<div align="center">

# 📝 StackEdit++ — Public Directory & Community Hub
### In-Browser Markdown Editor with LaTeX Math, Mermaid Diagrams & Zero-Telemetry Local Storage

[![Web App](https://img.shields.io/badge/Web%20App-Live%20Editor-success?style=flat-square&logo=google-chrome)](https://stackeditplusplus.meshworld.in/app)
[![Product Site](https://img.shields.io/badge/Product%20Site-StackEdit++-blue?style=flat-square)](https://stackeditplusplus.meshworld.in)
[![Zero Telemetry](https://img.shields.io/badge/Privacy-100%25%20Client--Side%20RAM-success?style=flat-square)](docs/privacy-architecture.md)
[![Offline PWA](https://img.shields.io/badge/PWA-Offline%20Capable-blueviolet?style=flat-square)](docs/recipes/offline-pwa-data-retention.md)
[![KaTeX Math](https://img.shields.io/badge/KaTeX-0.16.x-orange?style=flat-square)](docs/recipes/katex-macros-and-math.md)
[![Mermaid Diagrams](https://img.shields.io/badge/Mermaid-11.x-ff69b4?style=flat-square)](docs/recipes/mermaid-diagram-patterns.md)

**[Launch Live Editor](https://stackeditplusplus.meshworld.in/app) • [Product Homepage](https://stackeditplusplus.meshworld.in) • [Submit Feedback](https://github.com/cooldashing24/stackedit-community/issues/new?template=feedback.yml) • [Report a Bug](https://github.com/cooldashing24/stackedit-community/issues/new?template=bug_report.yml) • [Request Feature](https://github.com/cooldashing24/stackedit-community/issues/new?template=feature_request.yml)**

</div>

---

## ⚡ What is StackEdit++?

**[StackEdit++](https://stackeditplusplus.meshworld.in)** is an advanced, in-browser Markdown editor that renders LaTeX mathematical formulas, Mermaid diagrams, ABCjs sheet music, and syntax-highlighted code blocks in real time as you type.

All documents stay strictly inside your browser's process memory (RAM) and local sandboxed storage (IndexedDB). It operates offline with full Progressive Web App (PWA) capabilities and zero third-party telemetry.

### The Enterprise Compliance Dilemma
Under **SOC 2 Type II, HIPAA, GDPR, and ISO/IEC 27001**, corporate security policies explicitly forbid engineers, product architects, and healthcare researchers from pasting proprietary technical specifications, security threat models, cryptographic designs, or confidential meeting notes into cloud-based web editors that stream keystrokes to third-party remote servers.

**StackEdit++ was architected specifically to solve this dilemma:**
* 🌍 **Zero Installation, Instant Access**: Accessible worldwide via modern web browsers at [https://stackeditplusplus.meshworld.in/app](https://stackeditplusplus.meshworld.in/app) with zero native dependencies.
* 🔒 **100% Client-Side In-Browser Execution**: Markdown AST generation, KaTeX math parsing, and Mermaid vector compilation execute exclusively inside local browser memory.
* 🚫 **Zero Server Keystroke Telemetry**: No document content, draft notes, or intellectual property are ever transmitted to any remote backend server.
* ✈️ **Offline & Air-Gapped Capable**: Operates seamlessly in secure corporate networks, air-gapped workstations, or on airplanes with zero internet connectivity once loaded.

---

## 🛠️ Flagship Features & Verified Technical Guides

| Feature Area | Interactive Workbench | Authoritative Technical Guide | Use Cases & Production Scenarios |
| :--- | :--- | :--- | :--- |
| **Mathematical Typesetting** | [Live Editor Math Mode](https://stackeditplusplus.meshworld.in/app) | [KaTeX Notation & Macro Guide](docs/recipes/katex-macros-and-math.md) | • Academic papers, research manuscripts, and theorem proofs.<br>• Linear algebra matrices, calculus integrations, and Dirac notation.<br>• Instant client-side rendering without external font lag. |
| **Code-Defined Diagrams** | [Live Editor Diagramming](https://stackeditplusplus.meshworld.in/app) | [Mermaid Blueprints Catalog](docs/recipes/mermaid-diagram-patterns.md) | • Distributed systems and microservices sequence diagrams.<br>• State machines, CI/CD pipelines, and entity relationships.<br>• Rendered directly to scalable SVGs inside browser RAM. |
| **Offline PWA & Storage** | [Offline Progressive Web App](https://stackeditplusplus.meshworld.in/app) | [Data Retention & Storage Guide](docs/recipes/offline-pwa-data-retention.md) | • Air-gapped drafting in high-security enterprise environments.<br>• Instant persistence to IndexedDB with zero cloud exposure.<br>• Eviction prevention and local backup best practices. |
| **Enterprise Privacy** | [Zero-Telemetry Sandbox](https://stackeditplusplus.meshworld.in) | [Privacy Architecture Reference](docs/privacy-architecture.md) | • SOC 2, HIPAA, and GDPR compliance validation.<br>• Strict browser heap isolation and zero keystroke egress.<br>• Self-hosted Docker & on-premises architecture. |

---

## 🌐 Directory of Editor Capabilities

### 📐 Scientific & Mathematical Notation (KaTeX)
* **Inline Math (`$ ... $`)**: Typeset symbols ($e^{i\pi} + 1 = 0$) seamlessly inside sentences.
* **Block Math (`$$ ... $$`)**: Full-width display mode for complex equations, integrals, and limits.
* **Matrix Environments**: Complete support for `matrix`, `pmatrix`, `bmatrix`, and `vmatrix`.
* **Piecewise Cases**: Clean piecewise function definitions via `\begin{cases} ... \end{cases}`.
* **Custom LaTeX Macros**: Declare reusable document macros using `\gdef` to reduce formula verbosity.

### 📊 Code-Defined Diagramming (Mermaid 11.x)
* **Architecture Flowcharts (`flowchart TD / LR`)**: Map network ingress, service meshes, and VPC topologies.
* **Sequence Flows (`sequenceDiagram`)**: Document zero-trust auth handshakes, token rotations, and RPC calls.
* **State Machines (`stateDiagram-v2`)**: Specify task lifecycles, draft statuses, and transition guards.
* **Class & ER Diagrams (`classDiagram`, `erDiagram`)**: Model relational databases and object-oriented abstractions.
* **Visual Charts (`xychart-beta`)**: Display metrics and comparative histograms right inside markdown documents.

### ✍️ Modern Technical Writing Engine
* **Extended GFM AST**: Full GitHub Flavored Markdown support, including task lists, footnotes, strikethrough, and tables.
* **Trigger-Agnostic Autocomplete**: Fast inline completions for Emoji (`:` shortcodes) and upcoming wiki-style `[[` cross-links.
* **Dynamic Table of Contents (TOC)**: Real-time document outline automatically generated from measured heading offsets.
* **Custom YAML Settings**: Line-by-line configuration preservation with an intuitive Basics visual inspector.
* **Sheet Music & Notation (ABCjs)**: Client-side musical stave and tablature rendering.
* **Multi-Format Export**: Export clean Markdown, standalone raw HTML, or high-fidelity styled PDFs via browser print engines.

---

## 💬 Community Channels & Feedback

We welcome feedback, suggestions, and workflow improvements from developers, researchers, and technical writers worldwide:

- **[Live In-App Feedback](https://stackeditplusplus.meshworld.in/app)**: Submit thoughts and UX feedback directly within the editor interface.
- **[GitHub Feedback Form](https://github.com/cooldashing24/stackedit-community/issues/new?template=feedback.yml)**: Share impressions or workflow enhancements.
- **[Bug Reports](https://github.com/cooldashing24/stackedit-community/issues/new?template=bug_report.yml)**: Report rendering inconsistencies or parser regressions with sanitized snippets.
- **[Feature Requests](https://github.com/cooldashing24/stackedit-community/issues/new?template=feature_request.yml)**: Propose new client-side markdown extensions, diagram engines, or export tools.

---

## 🛡️ Security, Privacy & Upstream Attribution

### Security Vulnerabilities
If you discover a potential security vulnerability (such as a parser XSS or storage isolation flaw), please review our [Security Policy](SECURITY.md) and submit a report via [GitHub Private Vulnerability Reporting](https://github.com/cooldashing24/stackedit-community/security/advisories/new). Do not open public issues for sensitive vulnerabilities.

### Upstream Open-Source Attribution
StackEdit++ is a proprietary fork maintained by **MeshWorldLabs**, built upon the open-source foundation of **StackEdit** (v5.15.4), originally created by **Benoit Schweblin** under the **Apache License 2.0**:
- **Upstream Repository**: [https://github.com/benweet/stackedit](https://github.com/benweet/stackedit)
- **License**: Apache License 2.0 ([http://www.apache.org/licenses/LICENSE-2.0](http://www.apache.org/licenses/LICENSE-2.0))

All community technical guides and recipes in this repository are licensed under [CC BY 4.0 and MIT](LICENSE).

# Privacy Architecture & Client-Side Execution Model

> **Author**: StackEdit++ Engineering Team  
> **Platform**: [https://stackeditplusplus.meshworld.in](https://stackeditplusplus.meshworld.in)  
> **Editor**: [https://stackeditplusplus.meshworld.in/app](https://stackeditplusplus.meshworld.in/app)

---

## Executive Summary

Technical professionals, systems architects, security engineers, and researchers frequently draft sensitive documentation, including system architecture diagrams, cryptographic threat models, internal API designs, and confidential meeting notes. However, strict data governance policies under **SOC 2 Type II, HIPAA, GDPR, PCI-DSS, and ISO/IEC 27001** explicitly prohibit pasting proprietary technical specs or intellectual property into third-party cloud editors that stream keystrokes to remote servers or train AI models on user submissions.

**StackEdit++** was architected from the ground up as a **zero-telemetry, air-gapped in-browser Markdown editor**. Delivered instantly via edge networks, every keystroke, markdown AST parse, KaTeX mathematical formula evaluation, and Mermaid diagram compilation executes **100% client-side inside the local browser process memory (RAM)**.

---

## Architectural Isolation Boundary

```
┌────────────────────────────────────────────────────────────────────────┐
│             GLOBAL WEB DELIVERY (https://stackeditplusplus.meshworld.in)│
│                                                                        │
│   ┌────────────────────────────────────────────────────────────────┐   │
│   │                 In-Browser Process Memory Sandbox              │   │
│   │                                                                │   │
│   │   [ Keystrokes & Markdown ]                                    │   │
│   │               │                                                │   │
│   │               ▼                                                │   │
│   │   [ In-Memory Parser Pipeline ]                                │   │
│   │   • markdown-it AST Compilation                                │   │
│   │   • KaTeX 0.16.x Math Engine                                   │   │
│   │   • Mermaid 11.x Diagram Engine                                │   │
│   │   • ABCjs Sheet Music Engine                                   │   │
│   │   • Prism Syntax Highlighting                                  │   │
│   │               │                                                │   │
│   │               ▼                                                │   │
│   │   [ DOM Virtual Tree & Split View Preview ]                    │   │
│   │                                                                │   │
│   │   * Ephemeral JS Heap & IndexedDB                              │   │
│   │   * Sandboxed Local Web Storage                                │   │
│   │   * Zero Keystroke Transmission                                │   │
│   └────────────────────────────────────────────────────────────────┘   │
└────────────────────────────────────────────────────────────────────────┘
                                    │
                         ✖  NO NETWORK TRANSMISSION
                                    │
                                    ▼
                     ┌─────────────────────────────┐
                     │   Remote Backend Servers    │
                     │   (Zero Document Access)    │
                     └─────────────────────────────┘
```

---

## Core Privacy Pillars

### 1. In-Browser Memory Execution (No Server AST)
When you type in the editor, no HTTP `POST` requests containing your notes or documents are dispatched. The markdown-it engine parses Markdown into tokens directly within your browser thread. Similarly, mathematical symbols (`$`, `$$`) are evaluated by KaTeX without any remote math-rendering API.

### 2. Local Persistence (IndexedDB & LocalStorage)
Documents are stored exclusively in your browser's local sandbox storage (IndexedDB / localStorage). Closing the browser or losing internet connectivity does not compromise your work:
- Your files remain physically on your device.
- Clearing your browser cache or site data resets this local workspace.
- Export options (Markdown, raw HTML, styled PDF via print engine) generate files directly in browser memory without intermediate server uploads.

### 3. PWA & Air-Gapped Operation
StackEdit++ installs as a Progressive Web Application (PWA) with a dedicated Service Worker:
- After initial page load, all JavaScript modules, styling sheets, web fonts, and parser dependencies are cached locally.
- The editor can run on airplanes, in air-gapped corporate labs, or during field work with zero active internet connection.
- Unlike traditional web apps, StackEdit++ does not load remote CDNs (such as unpkg or cdnjs) at runtime.

### 4. Zero Tracking & Telemetry
StackEdit++ contains no third-party behavioral analytics, keystroke recorders, heatmaps, or advertising trackers. Your documents belong solely to you.

---

## Compliance Reference Matrix

| Regulation / Standard | Requirement | StackEdit++ Guarantee |
| :--- | :--- | :--- |
| **SOC 2 Type II** | Confidentiality & Trust Services Criteria | Documents remain in customer browser memory; zero cloud ingest. |
| **HIPAA** | Safeguarding Protected Health Information (PHI) | No PHI data crosses the network wire during drafting or preview. |
| **GDPR (EU 2016/679)** | Data Minimization & Storage Limitation (Art. 5) | No personal or document data is transmitted or retained on remote servers. |
| **ISO/IEC 27001** | Control A.8.12 (Data Leakage Prevention) | Local processing prevents accidental leakage to public formatting APIs. |

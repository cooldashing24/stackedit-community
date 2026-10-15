# Contributing to the StackEdit++ Community Hub

Thank you for your interest in contributing to the **StackEdit++ Community Hub & Technical Reference**!

**StackEdit++** ([https://stackeditplusplus.meshworld.in](https://stackeditplusplus.meshworld.in)) is an in-browser Markdown editor that renders LaTeX math, Mermaid diagrams, and syntax-highlighted code as you type. All files stay strictly in your browser RAM and local IndexedDB, operating seamlessly offline as a progressive web app (PWA).

This repository serves as the official public directory, community issue tracker, feedback channel, and technical recipe bank.

---

## 🚦 Core Invariants & Contribution Rules

### 1. In-Browser Privacy & Zero-Telemetry Invariant
When proposing editor enhancements, extensions, or sharing recipes:
- Document editing, math typesetting (KaTeX), diagram compilation (Mermaid), and ABCjs sheet music generation must execute **100% client-side** in browser process memory.
- We do **not** accept features or integrations that require transmitting unencrypted markdown notes, documents, or AST payloads to remote proprietary cloud servers.

### 2. Downstream & Recipe Contributions
- Code and workflows submitted to `docs/recipes/` must demonstrate **how users, technical writers, academics, and engineers build upon StackEdit++** (e.g., custom KaTeX macros, Mermaid flowcharts, offline backup automation, PDF export pipelines).
- Do **not** submit PRs attempting to reverse-engineer, decompile, or copy internal proprietary code from the core application.

### 3. Absolute Privacy Mandate (Rule 0)
- **Zero Real Secrets or Confidential Notes**: Never post confidential proprietary documentation, API keys, database credentials, or personal identifying information (PII) in GitHub issues, feedback forms, or sample snippets.
- Use sanitized, mock technical documentation for all reproduction cases.

---

## Ways to Contribute

### 💡 Requesting Features & Syntax Extensions
Have an idea for a Markdown extension, diagram dialect, or editor capability?
1. Check existing issues on the [Issue Tracker](https://github.com/cooldashing24/stackedit-community/issues).
2. Open a **[Feature Request](https://github.com/cooldashing24/stackedit-community/issues/new?template=feature_request.yml)** outlining:
   - The technical writing or workflow friction it solves.
   - Example Markdown syntax and expected preview output.
   - Confirmation that the capability can run 100% client-side in the browser.

### 🐛 Reporting Bugs
Discovered an issue with preview rendering, KaTeX parsing, Mermaid diagrams, or offline caching?
1. Open a **[Bug Report](https://github.com/cooldashing24/stackedit-community/issues/new?template=bug_report.yml)**.
2. Include your browser engine, operating system, DevTools console log (if any), and a minimal sanitized Markdown snippet that reproduces the issue.

### 💬 Submitting Community Feedback
Want to share feedback or workflow suggestions?
- Submit via our **[Community Feedback Template](https://github.com/cooldashing24/stackedit-community/issues/new?template=feedback.yml)** or directly via the feedback form within the [Web Application](https://stackeditplusplus.meshworld.in/app).

### 📖 Contributing Technical Recipes
Have an effective workflow for LaTeX academic papers, software architecture diagrams, or offline note synchronization?
1. Fork this repository.
2. Create a new markdown recipe under `docs/recipes/<recipe-name>.md`.
3. Ensure all examples render cleanly in StackEdit++ and contain no proprietary corporate data.
4. Submit a Pull Request against the `main` branch.

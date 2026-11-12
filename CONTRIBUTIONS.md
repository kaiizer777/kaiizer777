# 🌐 Open-Source Contributions Log

A comprehensive record of upstream open-source contributions, engineering fixes, security enhancements, and architectural bug investigations by [Mohd Sufiyan (@kaiizer777)](https://github.com/kaiizer777).

---

## 📑 Table of Contents

- [Steel Browser](#-steel-browser)

---

## ⚡ Steel Browser

> **Repository:** [`steel-dev/steel-browser`](https://github.com/steel-dev/steel-browser)  
> **Ecosystem:** Open-source headless browser infrastructure and remote browser execution engine for AI agents, CDP orchestration, and web automation.

### Merged Engine & API Fixes

| PR | Module | Description |
| :--- | :--- | :--- |
| **[#414](https://github.com/steel-dev/steel-browser/pull/414)** | `browser-socket` | **Harden upgrade handler with error listener and outer guard**: Added a socket `'error'` listener, an outer try/catch guard, hardened 400 responses, and 7 wire-level regression tests for the HTTP upgrade path (malformed Host, bad target, half-close handling). |
| **[#410](https://github.com/steel-dev/steel-browser/pull/410)** | `api` / `selenium` | **Handle child process error in selenium service to prevent crash**: Attached an `'error'` listener to the spawned `java` child process so a missing JRE rejects the session request with HTTP 500 instead of crashing the whole API server. Added 7 unit tests. |
| **[#405](https://github.com/steel-dev/steel-browser/pull/405)** | `casting` | **Validate session ID from URL against active session**: Patched a critical security check in `/v1/sessions/:id/cast` where arbitrary IDs were accepted, preventing unauthorized callers from hijacking active screencasts and injecting mouse/keyboard events. |
| **[#389](https://github.com/steel-dev/steel-browser/pull/389)** | `api` | **Cleanup session when casting target page is not found**: Resolved a persistent Puppeteer CDP WebSocket connection leak when screencast clients requested closed or non-existent `pageId` / `pageIndex`. Added unit test suite with 5 regression tests. |

---
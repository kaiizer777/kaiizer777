# 🌐 Open-Source Contributions Log

A comprehensive record of upstream open-source contributions, engineering fixes, security enhancements, and architectural bug investigations by [Mohd Sufiyan (@kaiizer777)](https://github.com/kaiizer777).

---

## 📑 Table of Contents

- [Better Auth](#-better-auth)
- [Steel Browser](#-steel-browser)
  - [Architectural Vulnerability & Bug Reports](#architectural-vulnerability--bug-reports)

---

## 🛡️ Better Auth

> **Repository:** [`better-auth/better-auth`](https://github.com/better-auth/better-auth)  
> **Ecosystem:** Comprehensive TypeScript-first authentication & authorization framework with 15k+ GitHub stars and 200k+ weekly npm downloads.

### Active / In-Flight Pull Requests

| PR | Subsystem | Description & Status |
| :--- | :--- | :--- |
| [#12035](https://github.com/better-auth/better-auth/pull/12035) | `oauth-provider` | Make `allowedScopes` storable across database adapters for OAuth 2.1 server capabilities. |
| [#11906](https://github.com/better-auth/better-auth/pull/11906) | `session` | Fail closed when deleting sessions from secondary storage (Redis / KV fallback safety). |
| [#11886](https://github.com/better-auth/better-auth/pull/11886) | `2fa` | Durable secondary-storage reads for multi-factor two-factor challenges. |
| [#11833](https://github.com/better-auth/better-auth/pull/11833) | `two-factor` | Prevent TOTP code replay reuse within the 30-second validity window. |
| [#11776](https://github.com/better-auth/better-auth/pull/11776) | `generic-oauth` | Add opt-in `refreshToken` override for custom enterprise token exchange. |
| [#11775](https://github.com/better-auth/better-auth/pull/11775) | `generic-oauth` | Forward configured `redirectURI` and gate `codeVerifier` for custom `getToken`. |
| [#11769](https://github.com/better-auth/better-auth/pull/11769) | `cli` | Add opt-in `timestamptz` generation for Drizzle PostgreSQL adapters. |
| [#11758](https://github.com/better-auth/better-auth/pull/11758) | `db` | Ensure atomic `deleteUser` transactions and propagate pre-read errors in `deleteWithHooks`. |
| [#11752](https://github.com/better-auth/better-auth/pull/11752) | `oauth-proxy` | Produce compact state parameter to comply with RFC and provider URI size limits. |
| [#11736](https://github.com/better-auth/better-auth/pull/11736) | `oauth` | Clarify rejection reasons and support fallback resolution for `trustedProviders`. |
| [#11734](https://github.com/better-auth/better-auth/pull/11734) | `mongo-adapter` | Add `supportsJSON` configuration option for nested document mapping. |
| [#11717](https://github.com/better-auth/better-auth/pull/11717) | `mcp` | Resolve in-process JWKS verification failures on Cloudflare Workers edge runtime. |
| [#11710](https://github.com/better-auth/better-auth/pull/11710) | `core` | Expose `additionalFields` on callback user types for strict TypeScript DX. |
| [#11941](https://github.com/better-auth/better-auth/pull/11941) | `docs` | Document CLI check command exit codes for automated CI/CD pipelines. |

---

## ⚡ Steel Browser

> **Repository:** [`steel-dev/steel-browser`](https://github.com/steel-dev/steel-browser)  
> **Ecosystem:** Open-source headless browser infrastructure and remote browser execution engine for AI agents, CDP orchestration, and web automation.

### Merged Engine & API Fixes

| PR | Module | Issue | Description |
| :--- | :--- | :--- | :--- |
| **[#414](https://github.com/steel-dev/steel-browser/pull/414)** | `browser-socket` | — | **Harden upgrade handler with error listener and outer guard**: Follow-up to #413. Added a socket `'error'` listener, an outer try/catch guard, hardened 400 responses, and 7 wire-level regression tests for the HTTP upgrade path (malformed Host, bad target, half-close handling). |
| **[#410](https://github.com/steel-dev/steel-browser/pull/410)** | `api` / `selenium` | [#408](https://github.com/steel-dev/steel-browser/issues/408) | **Handle child process error in selenium service to prevent crash**: Attached an `'error'` listener to the spawned `java` child process so a missing JRE (`ENOENT`) rejects the session request with HTTP 500 instead of crashing the whole API server. Added 7 unit tests. |
| **[#405](https://github.com/steel-dev/steel-browser/pull/405)** | `casting` | [#404](https://github.com/steel-dev/steel-browser/issues/404) | **Validate session ID from URL against active session**: Patched a critical security check in `/v1/sessions/:id/cast` where arbitrary IDs were accepted, preventing unauthorized callers from hijacking active screencasts and injecting mouse/keyboard events. |
| **[#389](https://github.com/steel-dev/steel-browser/pull/389)** | `api` | [#388](https://github.com/steel-dev/steel-browser/issues/388) | **Cleanup session when casting target page is not found**: Resolved a persistent Puppeteer CDP WebSocket connection leak when screencast clients requested closed or non-existent `pageId` / `pageIndex`. Added unit test suite with 5 regression tests. |

### Architectural Vulnerability & Bug Reports

| Issue | Area | Severity / Type | Description & Analysis |
| :--- | :--- | :--- | :--- |
| — | `browser-socket` / `security` | Denial of Service (DoS) | **Unhandled exception in the HTTP upgrade handler**: `api/src/plugins/browser-socket/browser-socket.ts` parses upgrade query params via ``new URL(url, `http://${request.headers.host}`)`` outside any `try` / `catch`, so a malformed `Host` header or a malformed client-controlled request-target throws `TypeError: Invalid URL` synchronously. Because the `upgrade` listener is `async`, the throw surfaces as an unhandled rejection that Node promotes to `uncaughtException`, taking the whole API server down on an unauthenticated request, severing every active session's control channel. The parse runs before handler routing, so all WebSocket upgrade requests are affected — `/v1/sessions/cast`, `/v1/sessions/logs`, `/v1/sessions/recording`, `/v1/sessions/pageId`, and the CDP proxy sockets. Self-assessed High (CVSS 3.1: 7.5, `AV:N/AC:L/PR:N/UI:N/S:U/C:N/I:N/A:H`; CWE-248 / CWE-754 / CWE-20). Hardened upstream in [#413](https://github.com/steel-dev/steel-browser/pull/413); follow-up hardening in [#414](https://github.com/steel-dev/steel-browser/pull/414). |
| [#408](https://github.com/steel-dev/steel-browser/issues/408) | `selenium` / `process` | Denial of Service (DoS) | **API server crashes when spawning Selenium without Java**: `SeleniumService.launch` spawned `java` without an `'error'` listener, so a missing JRE (`ENOENT`) raised an uncaught exception and took down the whole server on an unauthenticated `POST /v1/sessions` with `isSelenium: true`. Resolved in [#410](https://github.com/steel-dev/steel-browser/pull/410). |
| [#404](https://github.com/steel-dev/steel-browser/issues/404) | `casting` / `security` | Authentication Bypass | **Session ID from URL never validated**: `/v1/sessions/:id/cast` returned the global active session regardless of the path parameter, letting arbitrary callers stream live viewports and inject mouse/keyboard events. Resolved in [#405](https://github.com/steel-dev/steel-browser/pull/405). |
| [#395](https://github.com/steel-dev/steel-browser/issues/395) | `ui` / `memory` | Resource Leak | **WebSocket leak in `SessionLogs`**: Traced a component lifecycle leak where asynchronous teardown no longer closed the connection, leaking one socket per unmount on tab switches and console collapse until Node emitted `MaxListenersExceededWarning`. Fixed upstream by the [#402](https://github.com/steel-dev/steel-browser/pull/402) UI overhaul. |
| [#388](https://github.com/steel-dev/steel-browser/issues/388) | `api` / `cdp` | Descriptor Leak | **Puppeteer CDP connection leak on invalid target page**: Provided an isolated Vitest reproduction proving Chromium CDP handles were never released when casting requests a missing `pageId` / `pageIndex`. Resolved in [#389](https://github.com/steel-dev/steel-browser/pull/389). |

---

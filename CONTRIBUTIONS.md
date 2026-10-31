# 🌐 Open-Source Contributions Log

A comprehensive record of upstream open-source contributions, engineering fixes, security enhancements, and architectural bug investigations by [Mohd Sufiyan (@kaiizer777)](https://github.com/kaiizer777).

---

## 📑 Table of Contents

- [Better Auth](#-better-auth)
- [Steel Browser](#-steel-browser)

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
| **[#405](https://github.com/steel-dev/steel-browser/pull/405)** | `casting` | [#404](https://github.com/steel-dev/steel-browser/issues/404) | **Validate session ID from URL against active session**: Patched a critical security check in `/v1/sessions/:id/cast` where arbitrary IDs were accepted, preventing unauthorized callers from hijacking active screencasts and injecting mouse/keyboard events. |
| **[#389](https://github.com/steel-dev/steel-browser/pull/389)** | `api` | [#388](https://github.com/steel-dev/steel-browser/issues/388) | **Cleanup session when casting target page is not found**: Resolved a persistent Puppeteer CDP WebSocket connection leak when screencast clients requested closed or non-existent `pageId` / `pageIndex`. Added unit test suite with 5 regression tests. |

---

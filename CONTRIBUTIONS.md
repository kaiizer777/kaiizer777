# 🌐 Open-Source Contributions Log

A comprehensive record of upstream open-source contributions, engineering fixes, security enhancements, and architectural bug investigations by [Mohd Sufiyan (@kaiizer777)](https://github.com/kaiizer777).

---

## 📑 Table of Contents

- [Better Auth](#-better-auth)
  - [Featured & Merged Contributions](#featured--merged-contributions)
  - [Categorized Merged PRs & Commits](#categorized-merged-prs--commits)
  - [Active / In-Flight Pull Requests](#active--in-flight-pull-requests)
- [Steel Browser](#-steel-browser)
  - [Merged Engine & API Fixes](#merged-engine--api-fixes)
  - [Interface & UI Fixes](#interface--ui-fixes)
  - [Architectural Vulnerability & Bug Reports](#architectural-vulnerability--bug-reports)
- [Summary Statistics](#-summary-statistics)

---

## 🛡️ Better Auth

> **Repository:** [`better-auth/better-auth`](https://github.com/better-auth/better-auth)  
> **Ecosystem:** Comprehensive TypeScript-first authentication & authorization framework with 15k+ GitHub stars and 200k+ weekly npm downloads.

### Featured & Merged Contributions

| PR / Commit | Area | Description | Impact |
| :--- | :--- | :--- | :--- |
| [#11687](https://github.com/better-auth/better-auth/pull/11687) | `sso` | Allow rotating SAML IdP signing certificate with linked accounts | Prevents user lockout during enterprise IdP certificate rollover by decoupling public key verification from existing user identities. |
| [#11663](https://github.com/better-auth/better-auth/pull/11663) | `core` | Verify Microsoft Entra ID tokens when JWKS keys omit `alg` | Fixes token verification failures for Microsoft Entra ID / Azure AD endpoints where JWKS omit the optional `alg` parameter. |
| [`eaecb72`](https://github.com/better-auth/better-auth/commit/eaecb7229eeef5cfd763477b12f7dd2e44b89e51) (#11819) | `one-tap` | Apply Google provider `mapProfileToUser` and `getUserInfo` | Co-authored fix ensuring Google One Tap flows respect custom user mapping schemas and profile hooks. |
| [`3720d57`](https://github.com/better-auth/better-auth/commit/3720d57fb6234c52bdca23909024a09af1af26c9) (#11730) | `sso` | Accept SAML responses addressed to the `callbackUrl` ACS | Co-authored fix permitting SAML responses to target callback URL ACS endpoints without failing recipient validations. |

### Categorized Merged PRs & Commits

#### Core Engine & Authentication Protocols
* **[#11663](https://github.com/better-auth/better-auth/pull/11663)** — `core`: verify Microsoft Entra ID tokens when JWKS keys omit `alg`.
* **[`eaecb72`](https://github.com/better-auth/better-auth/commit/eaecb7229eeef5cfd763477b12f7dd2e44b89e51)** (`#11819`) — `one-tap`: apply Google provider `mapProfileToUser` and `getUserInfo` in one-tap plugin.
* **[#11499](https://github.com/better-auth/better-auth/pull/11499)** — `email-password`: corrected `APIMethod` contracts for email and password endpoint typings.
* **[#11497](https://github.com/better-auth/better-auth/pull/11497)** — `magic-link`: strict `APIMethod` contract enforcement and documented `rateLimit` options.

#### Enterprise SSO & Identity
* **[#11687](https://github.com/better-auth/better-auth/pull/11687)** — `sso`: allow rotating SAML IdP signing certificate with linked accounts.
* **[`3720d57`](https://github.com/better-auth/better-auth/commit/3720d57fb6234c52bdca23909024a09af1af26c9)** (`#11730`) — `sso`: accept SAML responses addressed to the `callbackUrl` ACS endpoint.
* **[#11703](https://github.com/better-auth/better-auth/pull/11703)** — `sso` docs: clarify SAML `callbackUrl` vs ACS endpoint behavior in v1.7.

#### Infrastructure, CLI & Ecosystem Tooling
* **[#11492](https://github.com/better-auth/better-auth/pull/11492)** — `rate-limit`: corrected the default rate limiting sliding window calculation.
* **[#11456](https://github.com/better-auth/better-auth/pull/11456)** — `chargebee`: fixed CLI migration generation command and updated migration guide.
* **[#11454](https://github.com/better-auth/better-auth/pull/11454)** — `contributing`: updated test helper import paths across test suites.
* **[#11453](https://github.com/better-auth/better-auth/pull/11453)** — `drizzle`: corrected CLI generation script arguments for Drizzle ORM schemas.

---

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

### Interface & UI Fixes

| PR | Module | Issue | Description |
| :--- | :--- | :--- | :--- |
| **[#396](https://github.com/steel-dev/steel-browser/pull/396)** | `ui` | [#395](https://github.com/steel-dev/steel-browser/issues/395) | **Close session logs WebSocket on unmount**: Fixed an effect cleanup bug in `SessionLogs` where WebSocket teardown was discarded, causing unbounded open socket leaks on tab switching and console collapse until Node fired `MaxListenersExceededWarning`. |

### Architectural Vulnerability & Bug Reports

| Issue | Area | Severity / Type | Description & Analysis |
| :--- | :--- | :--- | :--- |
| **[#408](https://github.com/steel-dev/steel-browser/issues/408)** | `api` / `selenium` | Denial of Service (DoS) | **API server crash when creating Selenium session without Java**: Identified that `spawn("java", ...)` lacks an unhandled `'error'` event listener in `SeleniumService.launch`. When Java is absent from container `$PATH`, an uncaught `ENOENT` terminates the entire Fastify process via unauthenticated `POST /v1/sessions`. |
| **[#404](https://github.com/steel-dev/steel-browser/issues/404)** | `casting` / `security` | Authentication Bypass | **Session ID from URL not validated**: Discovered that `/v1/sessions/:id/cast` returned the global active session regardless of the path parameter, permitting arbitrary URL callers to stream live viewports and inject input events. Resolved in [#405](https://github.com/steel-dev/steel-browser/pull/405). |
| **[#395](https://github.com/steel-dev/steel-browser/issues/395)** | `ui` / `memory` | Resource Leak | **WebSocket leak in SessionLogs**: Traced component lifecycle leak where asynchronous teardowns failed to close connections, exhausting Fastify server listener capacities. Addressed in [#396](https://github.com/steel-dev/steel-browser/pull/396). |
| **[#388](https://github.com/steel-dev/steel-browser/issues/388)** | `api` / `cdp` | Descriptor Leak | **Puppeteer CDP connection leak on invalid target page**: Provided isolated Vitest reproduction proving unmanaged Chromium CDP handles remained indefinitely when invalid target pages were queried. Resolved in [#389](https://github.com/steel-dev/steel-browser/pull/389). |

---

## 📈 Summary Statistics

- **Total Merged Contributions:** 13 PRs / Commits across high-scale TypeScript & Systems projects
- **Core Focus Areas:** Enterprise Authentication (SAML SSO, JWKS, OIDC), Distributed State, Headless Chromium CDP, WebSocket Lifecycle & Resource Management
- **Security & Integrity:** Resolved unauthorized WebSocket cast session access, prevented process crashes (DoS), and patched authentication token validation gaps.

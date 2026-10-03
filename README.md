<p align="center">
  <img src="https://raw.githubusercontent.com/kaiizer777/kaiizer777/main/assets/banner.svg" alt="Md Sufiyan Bari — Full Stack Engineer" width="100%">
</p>

<h1 align="center">Md Sufiyan Bari</h1>
<p align="center"><strong>Full Stack Engineer</strong> — building autonomous AI agents, self-hosted research engines, and production-grade SaaS.</p>

<p align="center">
  <a href="https://portfolio-sufiyan.pages.dev" target="_blank"><img alt="Portfolio" src="https://img.shields.io/badge/Portfolio-0EA5E9?style=for-the-badge&logo=googlechrome&logoColor=white"></a>
  <a href="mailto:mdsufiyanbari866@gmail.com"><img alt="Email" src="https://img.shields.io/badge/Email-mdsufiyanbari866%40gmail.com-EA4335?style=for-the-badge&logo=gmail&logoColor=white"></a>
  <a href="https://wa.me/918709914537" target="_blank"><img alt="WhatsApp" src="https://img.shields.io/badge/WhatsApp-%2B91%2087099%2014537-25D366?style=for-the-badge&logo=whatsapp&logoColor=white"></a>
  <a href="https://github.com/kaiizer777" target="_blank"><img alt="GitHub" src="https://img.shields.io/badge/GitHub-kaiizer777-181717?style=for-the-badge&logo=github&logoColor=white"></a>
  <a href="https://multiitenant.online" target="_blank"><img alt="Live SaaS" src="https://img.shields.io/badge/Live%20SaaS-multiitenant.online-6366F1?style=for-the-badge&logo=googlecloud&logoColor=white"></a>
</p>

---

## About

Self-taught full-stack engineer working across **Rust, Go, TypeScript, and Python**. I build end to end — browser-automation agents driving real Chromium over the DevTools Protocol, serverless AI orchestrators on AWS Lambda and Cloudflare Workers, and multi-tenant SaaS platforms with real payment infrastructure behind them.

Everything below is deployed, documented, and tested. None of it came from following a tutorial.

**Open to** remote Full Stack / AI engineering roles, and to interesting open source work.

---

## Featured Work

### Haunter

**Autonomous CI failure diagnosis, self-healing repair & security auditing.**

Wakes on a GitHub Actions failure via webhook, distills the log trace and failing diff, determines root cause, generates candidate patches, then verifies each one inside an **isolated zero-trust GitHub Actions sandbox mirror** seeded through the Git Data API — no `git clone`, no container runtime, no untrusted code on the orchestrator. Passes open an auditable PR; exhausted retries leave a structured root-cause comment instead.

Also ships a read-only **Auditor mode** (security, architecture, regressions, performance), an interactive **in-browser pairing studio** powered by StackBlitz WebContainer + Monaco, and a 20-fixture golden eval harness.

[![Live Dashboard](https://img.shields.io/badge/Live%20Dashboard-22D3EE?style=for-the-badge&logo=cloudflare&logoColor=black)](https://haunter.sufiyanx.workers.dev)
[![Source](https://img.shields.io/badge/Source-8B5CF6?style=for-the-badge&logo=github&logoColor=white)](https://github.com/kaiizer777/Haunter)

`Next.js 16` `React 19` `FastAPI` `Python 3.11` `Neon Postgres` `AWS Lambda` `Cloudflare Workers` `GitHub Actions` `Terraform` `WebContainer`

---

### mew-agent

**Rust-native computer-use agent that drives a visible Chromium session.**

An 8-crate Rust workspace where a natural-language command becomes real browser work. Perception is **accessibility-tree-first instead of screenshot-first**, cutting average snapshot size to roughly 2 KB versus the tens of KB a vision pass costs. Execution is a two-agent hybrid — a `ChatAgent` that handles conversation and planning, a `BrowserAgent` that does the clicking — wired through typed `Handoff` / `Result` contracts with mid-task steering.

29 shipped phases, including Reflexion-style episodic memory, supervisor heartbeat and respawn, and explicit user intervention channels.

[![Source](https://img.shields.io/badge/Source-EA4335?style=for-the-badge&logo=rust&logoColor=white)](https://github.com/kaiizer777/mew-agent)

`Rust` `Tokio` `Chrome DevTools Protocol` `Tauri 2` `TypeScript` `553 workspace tests` `313-case eval harness`

---

### onyx-research-agent

**Self-hosted AI web research engine — a $0/month operational budget.**

A ReAct agent loop sits on top of a parallel multi-provider discovery layer. SearXNG runs self-hosted and unlimited; TinyFish Search and Jina Reader/Search/Reranker act as free-tier parallel sources and fallbacks. If a target blocks one, Onyx routes to the next without operator intervention. Nothing is paid for until the free tiers are exhausted.

Deep Research mode decomposes a query into sub-questions, researches them in parallel across the full discovery layer, and compiles a cited markdown report. Everything lands in an embedded SQLite FTS5 knowledge lake, with a ticker scheduler daemon, a JSON HTTP API, and a fail-closed Telegram gateway on top.

[![Source](https://img.shields.io/badge/Source-00ADD8?style=for-the-badge&logo=go&logoColor=white)](https://github.com/kaiizer777/onyx-research-agent)

`Go` `Colly` `go-rod` `SQLite FTS5` `SearXNG` `Docker Compose` `Telegram API`

---

### Also built

| Project | What it does |
| :-- | :-- |
| **[MultiTenant SaaS](https://multiitenant.online)**<br>`Next.js 16` `Drizzle` `PostgreSQL` `BetterAuth` `Razorpay` `Groq` | B2B2C multi-tenant platform for service businesses — 100+ API routes, 33 tables, isolated per-tenant subdomains, GST-compliant invoicing with atomic payment allocation, application-layer AES-256-GCM encryption for PII with deterministic lookups, and a RAG-powered AI advisor with multi-key fallback. |
| **[SIH2026](https://github.com/kaiizer777/SIH2026)**<br>`Python` `Machine Learning` | Rockfall prediction system for the Ministry of Mines (SIH25071), fusing satellite SAR change detection, DEM terrain morphology, and physics-informed Fukuzono sensor dynamics with class-weighted training. Built end to end as primary developer after selection to the hackathon's offline round. |
| **[beat](https://github.com/kaiizer777/beat)**<br>`Java 21` `Spring Boot` `Next.js` | Personalized news research digest — user-defined topic channels with scheduled delivery, backed by an AI pipeline that delivers clean digests over email and web. |

---

## Open Source

### Better Auth — 6 merged documentation PRs

[![npm downloads/week](https://img.shields.io/npm/dw/better-auth?style=for-the-badge&label=npm%20downloads%2Fweek&color=8B5CF6&logo=npm&logoColor=white)](https://www.npmjs.com/package/better-auth)

Better Auth is the most comprehensive TypeScript authentication framework and one of the highest-adoption auth libraries in the ecosystem. I don't maintain it — but my documentation PRs ship inside it, which means the setup guides people use to get authentication working are ones I helped fix.

| PR | Contribution |
| :-- | :-- |
| [#11499](https://github.com/better-auth/better-auth/pull/11499) | `docs(email-password)` — corrected `APIMethod` contracts |
| [#11497](https://github.com/better-auth/better-auth/pull/11497) | `docs(magic-link)` — corrected the `APIMethod` contract and documented `rateLimit` |
| [#11492](https://github.com/better-auth/better-auth/pull/11492) | `docs(rate-limit)` — corrected the default window |
| [#11456](https://github.com/better-auth/better-auth/pull/11456) | `docs(chargebee)` — fixed the CLI command and updated migration guidance |
| [#11454](https://github.com/better-auth/better-auth/pull/11454) | `docs(contributing)` — updated the test helper import |
| [#11453](https://github.com/better-auth/better-auth/pull/11453) | `docs(drizzle)` — updated the CLI command in the adapter guide |

---

## Stack

**Languages** — TypeScript · JavaScript · Python · Go · Rust · SQL

![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white) ![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white) ![Go](https://img.shields.io/badge/Go-00ADD8?style=flat-square&logo=go&logoColor=white) ![Rust](https://img.shields.io/badge/Rust-000000?style=flat-square&logo=rust&logoColor=white) ![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)

**Frontend** — Next.js · React · Tailwind CSS · Framer Motion · Three.js · GSAP

![Next.js](https://img.shields.io/badge/Next.js-000000?style=flat-square&logo=nextdotjs&logoColor=white) ![React](https://img.shields.io/badge/React-61DAFB?style=flat-square&logo=react&logoColor=black) ![Tailwind CSS](https://img.shields.io/badge/Tailwind-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white) ![Framer Motion](https://img.shields.io/badge/Framer%20Motion-0055FF?style=flat-square&logo=framer&logoColor=white) ![Three.js](https://img.shields.io/badge/Three.js-000000?style=flat-square&logo=threedotjs&logoColor=white)

**Backend** — Node.js · FastAPI · REST · GraphQL · WebSockets

![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat-square&logo=nodedotjs&logoColor=white) ![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white) ![GraphQL](https://img.shields.io/badge/GraphQL-E10098?style=flat-square&logo=graphql&logoColor=white)

**Data** — PostgreSQL · MongoDB · SQLite · Drizzle · Prisma · Redis

![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white) ![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=flat-square&logo=mongodb&logoColor=white) ![SQLite](https://img.shields.io/badge/SQLite-003B57?style=flat-square&logo=sqlite&logoColor=white) ![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat-square&logo=redis&logoColor=white)

**Infrastructure** — AWS Lambda · Cloudflare Workers · Vercel · Docker · Terraform · Redis

![AWS Lambda](https://img.shields.io/badge/AWS%20Lambda-FF9900?style=flat-square&logo=amazonwebservices&logoColor=black) ![Cloudflare](https://img.shields.io/badge/Cloudflare-F38020?style=flat-square&logo=cloudflare&logoColor=white) ![Vercel](https://img.shields.io/badge/Vercel-000000?style=flat-square&logo=vercel&logoColor=white) ![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white) ![Terraform](https://img.shields.io/badge/Terraform-7B42BC?style=flat-square&logo=terraform&logoColor=white)

**AI** — Groq · OpenAI-compatible APIs · RAG pipelines · prompt engineering · agent orchestration

![Groq](https://img.shields.io/badge/Groq-F55036?style=flat-square&logo=groq&logoColor=white) ![OpenAI](https://img.shields.io/badge/OpenAI-412991?style=flat-square&logo=openai&logoColor=white) ![Anthropic](https://img.shields.io/badge/Anthropic-D4A27F?style=flat-square&logo=anthropic&logoColor=white) ![RAG](https://img.shields.io/badge/RAG-FF6B6B?style=flat-square)

**Auth & Security** — BetterAuth · OAuth · AES-256-GCM · RBAC · CSRF · CSP

![Better Auth](https://img.shields.io/badge/BetterAuth-7C3AED?style=flat-square&logo=better-auth&logoColor=white) ![OAuth](https://img.shields.io/badge/OAuth-000000?style=flat-square&logo=oauth&logoColor=white)

---

## Education

**B.E. Information Technology** — Rajiv Gandhi Institute of Technology (RGIT), Andheri, Mumbai
Expected graduation **2029**. Selected to the offline round of a competitive hackathon as primary developer, building the project end to end.

---

<p align="center">
  <sub>Portfolio — <a href="https://portfolio-sufiyan.pages.dev" target="_blank">portfolio-sufiyan.pages.dev</a> &nbsp;·&nbsp; <a href="https://github.com/kaiizer777/kaiizer777" target="_blank">Profile source</a></sub>
</p>
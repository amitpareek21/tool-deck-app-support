# ToolDeck Support — Product roadmap (2026)

This file is the **canonical phase plan** for ToolDeck Support. Cursor and contributors should use it to **sequence work**, **stay aligned on scope**, and **track completion** (update checkboxes when a slice is truly done and merged).

_Last reviewed: 2026-04-17._

---

## How to use this in Cursor

- Prefer implementing work **in phase order** unless a later phase is explicitly unblocked and small.
- When starting a task, **quote the phase and bullet** you are implementing (in chat or PR text).
- After shipping a bullet, **check the box** in this file in the same PR (or immediately after merge) so history stays honest.

---

## Phase 1: The Brain (knowledge ingestion)

- [x] **Initialize:** Laravel 13 + Inertia + React (TypeScript via Breeze). *Requires PHP ^8.3 (`composer.json`).*
- [ ] **DB setup:** Configure PostgreSQL with the `pgvector` extension.
- [ ] **Schema:** Create `Document` and `Chunk` models with vector support.
- [ ] **Ingestion:** Build `ScraperService` for Markdown-based ingestion.
- [ ] **Pipeline:** HTML → Markdown → semantic chunking → vector embedding.

## Phase 2: The Thinker (agentic RAG)

- [ ] **Agent logic:** Implement `SupportAgent` using the Laravel AI SDK.
- [ ] **Retrieval:** Build multi-query retrieval for higher search accuracy.
- [ ] **Logic loop:** Implement a ReAct-style (reasoning + acting) loop.
- [ ] **Validation:** Add a self-correction / grounding layer to reduce incorrect factual claims (tune metrics with the team).

## Phase 3: The Tooling (action layer)

- [ ] **PHP tools:** Define Laravel AI **Tools** (function calling), e.g.:
  - `fetchOrderDetails()`
  - `resetUserPassword()`
- [ ] **Integration:** Wire tools into `SupportAgent`.

## Phase 4: The Human Bridge (B2B SaaS)

- [ ] **Dashboard:** Inertia/React dashboard for human oversight.
- [ ] **Sockets:** Real-time monitoring via Laravel Reverb.
- [ ] **Takeover:** One-click “human takeover” mode.

## Phase 5: Distribution and scale

- [ ] **Widget:** Embeddable React widget (script tag).
- [ ] **Tenancy:** Strict vector data isolation per client.

---

## Out of scope (until listed above)

Details like billing, marketing site, or mobile apps are **not** implied by this roadmap unless added here explicitly.

# ToolDeck Support

ToolDeck Support is part of **ToolDeck**, a **B2B AI resolution engine**: structured workflows for support and operations—not one-off prompts in a chat box.

## Roadmap

**[`ROADMAP.md`](ROADMAP.md)** is the single source of truth for scope and sequencing. Prefer work in **phase order** (Phase 1 → 5); when you ship a bullet, update its checkbox in `ROADMAP.md` in the same change when practical.

| Phase | Focus | Highlights |
| --- | --- | --- |
| **1** — The Brain | Knowledge ingestion | PostgreSQL + **pgvector**, `Document` / `Chunk`, Markdown ingestion, HTML → Markdown → chunking → embeddings |
| **2** — The Thinker | Agentic RAG | `SupportAgent` (Laravel AI), multi-query retrieval, ReAct-style loop, grounding / self-correction |
| **3** — The Tooling | Action layer | Laravel AI **Tools** (e.g. order lookup, password reset), wired into the agent |
| **4** — The Human Bridge | B2B SaaS | Inertia/React oversight dashboard, Laravel Reverb, human takeover |
| **5** — Distribution | Scale | Embeddable widget, strict per-tenant vector isolation |

**Out of scope** until it appears in `ROADMAP.md`: billing, marketing site, mobile apps, and similar product work not listed above.

### Status (from `ROADMAP.md`)

- **Done:** Phase 1 — Initialize (Laravel 13 + Inertia + React with TypeScript via Breeze).
- **Next:** Phase 1 — DB setup (PostgreSQL + `pgvector`), then schema, ingestion, and pipeline bullets.

## Stack

- **Backend:** Laravel 13, PHP ^8.3+ (see [`composer.json`](composer.json)); PostgreSQL with **pgvector** (target for Phase 1).
- **Frontend:** Inertia.js, React (TSX), Tailwind CSS.
- **AI (upcoming per roadmap):** **Laravel AI** (`Laravel\AI`) for agents and tools—no ad-hoc HTTP clients to model providers on product paths.

## Where logic should live

- **`app/Services/AI`** — Orchestration, retrieval, resolution steps.
- **`app/Agents`** — Class-based agents (e.g. support triage / resolution).
- **`app/Tools`** — Function-calling tools for agents.
- **`resources/js/Components/Widget`** — Embeddable customer widget (Phase 5).

## Local development

Requirements: PHP ^8.3, Composer, Node.js + npm, and (for upcoming work) PostgreSQL with `pgvector`.

```bash
cp .env.example .env
php artisan key:generate
composer install
npm install
```

Point **`DB_*`** in `.env` at your database (SQLite is fine for auth/UI-only work today; Phase 1 expects PostgreSQL + pgvector).

```bash
php artisan migrate
npm run dev
```

Run the full dev stack (HTTP server, queue worker, log tail, Vite):

```bash
composer run dev
```

Alternatively, run `php artisan serve` and `npm run dev` in separate terminals.

```bash
php artisan test
npm run build
```

## Contributing

Follow **`ROADMAP.md`** for what to build and in what order. In PRs or reviews, cite the **phase and bullet** you are implementing.

## Security

If you find a security issue, report it privately to the project maintainers instead of opening a public issue.

## License

This application is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).

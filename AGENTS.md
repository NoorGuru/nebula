# AGENTS.md — Nebula

Static Astro site (`npm run build`). Content collection: `src/content/ideas/*.md` validated by `src/content.config.ts`.

## When user asks for a new country batch or more ideas

Do NOT launch researcher agents immediately. Follow this sequence every time.

### 1. Study current state first
- Read `research/<existing>-brief.md`, `research/country-brief.template.md`, `src/content.config.ts`, and 2-3 files in `src/content/ideas/` for tone Depths (problem / why-it-worked / challenges / funding / latest + Arabic summary).

### 2. Agree on the brief BEFORE any research agents
Ask and lock these (use `request_user_input` when interactive):
1. **Scope**: country, slot count (default 12; KSA precedent: 16), news window (default RELAXED: any date is fine, ideas first — prefer the freshest citable item and record its date; strict 3-month window only if the user asks, Egypt precedent).
2. **Diversity quotas**: max 2 per sector; ≥3 distinct stages (seed / Series A / Series B+ / late-stage-public / acquired / closed); outcome mix — default 11 operating + exactly 1 `closed`/`failed` with `challenges` filled; whether to allow `status=idea` paper-stage ideas (KSA: yes, 1-2).
3. **Schema**: always the expanded set (KSA default — do NOT ask). Base fields: `title, summary, tags, featured, publishedAt, company, country, sector, stage, founded, amountRaised, amountSource, valuation, valuationSource, status, coreProblem, whyItWorked, challenges, sources[{title,url}], summaryAr`. Expanded: add `howItWorks, painPoints, businessModel, founders, hqCity, usersMetrics, competitors, license, vision2030Fit (reused as the batch country's strategy fit), investors`. Only use fields the renderer/schema actually supports — check `src/content.config.ts` + `src/pages/idea/[...slug].astro` first.
4. **Evidence**: ≥1 INSPECTED EN source per startup (open the body via fetch — snippets are not evidence; AR source optional). Prefer primary (company blog, filings, reputable press). NEVER invent numbers/names/dates — OMIT the frontmatter key when unverifiable (only `amountSource`/`valuationSource` may carry the literal `MISSING`). `summaryAr`: one-sentence MSA Arabic, self-translated when sources are EN-only. Idea-stage: founder/accelerator pages count; funding expected `MISSING`.
5. **Output**: files directly (table-first research FAILED 3× with zero rows — do not use it). Agents research AND write `src/content/ideas/<slug>.md` with disjoint slug sets (2–3 each).

Write the locked brief to `research/<country>-brief.md` (copy from `research/country-brief.template.md`) and wait for user's `go`.

### 3. Research + write (multi-agent, after `go`)
- Fan out with Workflow: 5 writer-agents × 2–3 startups (disjoint slugs). Estimate ~5 agents, ~10-20 min for 13–16 ideas.
- Each writer-agent READS this file + the country brief + `src/content.config.ts` + one good example file, then researches (search + OPEN every cited source body) AND writes its own files with DISJOINT slug sets (2–3 each). Complete = files delivered with omissions, never held back for missing fields.
- Per startup capture: problem solved, how they do it, pain points, how they make money, ≥1 inspected EN source, self-written `summaryAr`.
- Replacement policy: if a candidate won't verify (no openable source, unprovable closure), swap it for a citable alternative in the same slot and record the swap — never stall the batch. Quotas are enforced by the parent at the end, not by a synthesizer agent.

### 4. Verify (parent, every batch)
- File conventions: slug = kebab company name; `tags` must include country tag; `country` = full name; `status` in `operating|acquired|closed|failed|idea`.
- Tag discipline (every batch): reuse existing tags from `src/lib/tagAr.ts` — the single source of truth for the MSA Arabic titles shown on `/tags`. Any NEW tag must add its Arabic title to that map in the same change, or the tag renders English-only. Keep tag spelling identical across files sharing a sector (one tag page per sector — never `sportstech` next to `sports-tech`). Canonical consolidated spellings (use these, never the hyphenated variants): `ecommerce` (NOT `e-commerce` — consolidated 2026-09-28 across all idea files; the `e-commerce` key was removed from `tagAr.ts`). The renderer only links `country`/`sector` breadcrumbs when a matching tag page exists, but prefer values that match an existing tag anyway. Concurrent batches share this file — re-read `src/lib/tagAr.ts` immediately before editing (a parallel batch may have rewritten it and silently dropped your entries; observed 2026-09-28) and re-verify your entries are still present after the build. Country cards on `/tags` use one uniform accent — do not add per-country colors; a hue must encode something real (idea-card status colors are the only evidence-backed accents).
- `npm run build` must be green (repo has NO test harness — build is the gate), plus file-count check and 2–3 lede spot-checks.
- Lede rule (never break): `title` + `summary` state THE IDEA in English (what the company does/is), never the fundraise or latest news — funding lives in `## Funding` / `## Latest` only. `summaryAr` is the same idea in MSA Arabic; translate it yourself when sources are EN-only (and vice versa).
- Body sections: `## The problem / ## How it works / ## Pain points / ## Business model / ## Challenges / ## Funding / ## Latest — <Mon YYYY>` (dated items only, no invented dates).
- Run `npm run build` and fix schema errors. Never commit/push unless explicitly asked.


# Frontier Brief — Nebula (12 slots, any-country)

Locked 2026-10-06. See `AGENTS.md` for the reusable flow.
Track name: **frontier** (tag `frontier` = "أفكار رائدة"). This is a cross-country
track, not a country batch — one idea per slot can come from anywhere.

## 1. Scope

- Country: ANY (per-idea `country` = full English name, e.g. `Japan`;
  `tags` must include the matching country tag AND `frontier`).
- News window: RELAXED 2026-10-06 — any date is fine, ideas first. Prefer the
  freshest citable item per startup and record its date in `## Latest`;
  never invent dates.
- Slots: 12 ideas total.
- Bar (locked): **frontier tech or tech-assisted only** — AI/robotics/space/
  biotech/energy-climate/semiconductors-compute/advanced-manufacturing plus
  wild tech-assisted bets. Dull/normal startups are REJECTED even if fundable.
  Pure paper concepts from nowhere are allowed ONLY as the 1–2 `idea` slots
  below (must still push things forward, tech-led).

## 2. Diversity quotas (must all hold)

- Sector mix, max 2 per sector (frontier sectors: ai, robotics, space,
  biotech, energy, climate/climatetech, semiconductors, manufacturing,
  healthtech-deep, mobility-deep e.g. eVTOL/autonomy).
- Stage mix, >= 3 distinct stages (seed / Series A / Series B+ /
  late-stage-public / acquired / idea). Expect early-stage heavy.
- Outcome mix: 9–10 operating/acquired + exactly 1 `closed`/`failed` with
  `challenges` filled + 1–2 paper-stage (`status: idea`, funding `MISSING`).
- Any-country spread: max 2 ideas per country.

## 3. Evidence rules

- NEVER invent numbers/names/dates. `amountRaised` / `valuation` / `founded`
  only from citable sources; otherwise omit the frontmatter key (only
  `amountSource`/`valuationSource` may carry the literal `MISSING`).
- Each idea: >= 1 INSPECTED EN source `{title, url}` (open the body via fetch
  — snippets are not evidence; AR source optional). Prefer primary (company
  blog, filings, reputable press). Paper-stage (`idea`): founder/accelerator/
  paper page counts as source; funding expected `MISSING`.
- Per idea capture: problem solved, how they do it, pain points, how they
  make money. `summaryAr` (one-sentence MSA Arabic) REQUIRED for every idea —
  self-translate when sources are EN-only.
- Lede rule: `title` + `summary` state THE IDEA in English (what it does),
  never the fundraise or latest news — funding lives in `## Funding` /
  `## Latest` only.

## 4. Schema plan (expanded set + frontier tag)

Base + expanded (`src/content.config.ts` — all optional except base):
`title, summary, tags, featured, publishedAt, company, country, sector, stage,
founded, amountRaised, amountSource, valuation, valuationSource, status,
coreProblem, whyItWorked, challenges, sources, summaryAr` +
`howItWorks, painPoints, businessModel, founders, hqCity, usersMetrics,
competitors, license, vision2030Fit (reused as the batch country's strategy
fit — for frontier ideas use the startup's home-country strategy fit or omit),
investors`.
- `tags`: must include `frontier` + country tag + sector tag(s). `frontier`
  is NEW — parent adds `frontier: 'أفكار رائدة'` to `src/lib/tagAr.ts` in the
  same change (tag-discipline rule).
- `status` in `operating|acquired|closed|failed|idea`. Slug = kebab company
  name. Reuse existing tag spellings (`ecommerce` never `e-commerce`).
- Body sections: `## The problem / ## How it works / ## Pain points /
  ## Business model / ## Challenges / ## Funding / ## Latest — <Mon YYYY>`
  (dated items only).

## 5. Special design (locked: badge + card)

- New `frontier` tag + distinct card accent/badge (`Card.astro`, global.css),
  homepage `⚡ Frontier` filter pill (`index.astro` flashcards `isFrontier`),
  idea-page banner (`[...slug].astro`, same hue as card accent so the color
  encodes one real thing). Country cards on `/tags` stay uniform — no
  per-country colors. Parent implements design + tagAr entry; writers only
  add the `frontier` tag (never invent CSS).
- Gate: `npm run build` green (no test harness) + file-count + 2–3 lede
  spot-checks.

## 6. Execution plan (after `go`)

1. Parent: design patch (`tagAr.ts` frontier entry, `Card.astro` accent,
   `index.astro` filter, `[...slug].astro` banner; `npm run build` green).
2. Workflow: 5 writer-agents × 2–3 startups with DISJOINT slug sets
   (writers read this brief + `src/content.config.ts` + one good example,
   research with every cited source body OPENED, and write files directly —
   table-first research is banned). Complete = files delivered with omissions,
   never held back for missing fields.
3. Replacement policy:if a candidate won't verify (no openable source,
   unprovable closure), swap it for a citable alternative in the same slot
   and record the swap — never stall the batch.
4. Parent verify: quotas, tag discipline (`frontier` + country + sector
   spellings), lede rule, build green. Never commit/push unless asked.

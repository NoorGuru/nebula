# Garage Brief — Nebula (10 slots, buildable-frontier pilot)

Locked 2026-10-06. See `AGENTS.md` for the reusable flow.
Track name: **garage** (tag `garage` = "أفكار الكراج"). Thesis: ideas that
would have sounded insane 3 years ago and are buildable today by ~2 people
with <$100k — arbitrage between newly-possible tech and unbuilt wedges.
Applied angle: global tech aimed at MENA gaps first, from-anywhere allowed.

## 1. Scope

- Country: MENA-first, anywhere allowed (per-idea `country` = the market the
  idea is built FOR, full English name; `tags` include `garage` + country tag).
- News window: NONE — these are original build briefs, not company teardowns.
  "Why now" must name a dated enabling shift (model release, API, price drop)
  with its date recorded, never invented.
- Slots: 10 ideas total (pilot — new format, smaller batch).
- Bar (locked, ALL THREE must hold):
  1. Would it have sounded insane 3 years ago? (else it's a normal startup)
  2. Can ~2 people start it for <$100k? Software only: no fab, no launchpad,
     no new science, no hardware runs — only assembly of existing infra
     (open models, commodity APIs, WhatsApp/app-store distribution).
  3. Is there a first customer who'd pay before it's finished? (a wedge with
     a named payer, not a vision deck)

## 2. Diversity quotas (must all hold)

- Max 2 ideas per wedge-domain (e.g. voice/dialects, field-ops, SMEs,
  fintech-plumbing, devtools, public-services, health-access, agrifood).
- >= 3 distinct enablers across the batch (e.g. open-weight LLMs, voice
  synthesis/recognition, vision models, messaging APIs, cheap maps/sensors).
- At least 3 ideas whose first customer is a named MENA segment (clinics,
  repair shops, small factories, smallholder farmers — payer must be real).
- Exactly 1 glorious-failure brief (`status: idea`, `challenges` explains the
  trap: regulation, unit economics, or distribution wall).

## 3. Evidence rules (adapted — no companies to cite)

- NEVER invent prices, product capabilities, or dates. Every build-cost
  figure and capability claim needs >= 1 INSPECTED source (open the body —
  snippets are not evidence): model/API docs, pricing pages, reputable press.
  If a price is unverifiable, write a range marked `~` or omit the key.
- Each brief's "why now" enabler must be a real dated thing (e.g. "open
  model X, <Mon YYYY>"), cited in `sources`.
- `summaryAr` (one-sentence MSA Arabic) REQUIRED, self-translated.
- Lede rule: `title` + `summary` state THE BUILD in English (what two people
  would make), never a market thesis. Funding sections do not exist here.

## 4. Schema plan (new short format)

New optional frontmatter (all `.default('')`, parent adds to
`src/content.config.ts` + renderer BEFORE writers):
`buildCost` (e.g. "~$15k: ..."), `techStack` (the assembly, no custom
silicon), `firstCustomer` (named payer + why they pay early), `whyNow`
(dated enabler, one line).
Also: `title, summary, tags (garage + country + domain), publishedAt
(write date), country, sector (= wedge-domain), stage ('idea'),
status ('idea'), coreProblem, howItWorks, challenges, sources, summaryAr`.
- `garage` is NEW — parent adds `garage: 'أفكار الكراج'` to `src/lib/tagAr.ts`
  in the same change. Reuse existing tag spellings elsewhere.
- Body sections (short): `## The problem / ## The build / ## Why now /
  ## First customer / ## Challenges` (no Funding/Latest — nothing raised,
  nothing launched).

## 5. Special design (to lock with user at build time)

- Default: same teal-family badge idiom as frontier? NO — teal already
  encodes frontier. Garage needs its own hue or a non-hue treatment
  (proposal: amber accent + "Garage" badge + homepage filter pill).
  Decided during parent design patch, before writers.

## 6. Execution plan (after `go`)

1. Parent: schema + renderer patch (`content.config.ts`, Card badge,
   index filter, detail rendering for buildCost/techStack/firstCustomer/
   whyNow; `npm run build` green).
2. Workflow: 4-5 writer-agents × 2–3 briefs with DISJOINT slugs (writers
   read this brief + config + one example, verify every price/claim
   against an opened source, write files directly — table-first banned).
3. Replacement policy: if a brief's enabler won't verify, swap the brief,
   record the swap — never stall.
4. Parent verify: 3-bar test per brief, quotas, tag discipline, lede rule,
   build green. Never commit/push unless asked.

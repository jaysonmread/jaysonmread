# CC Blues — Wiki, Archive, Experience: the three things, and how they complete each other

_Scribed 2026-07-08. Substrate: `My Drive / CC Blues Archive V2`. Author builds the back-end presentation; content trickles in piece by piece._

---

## 0. Why this doc exists

We keep saying "the wiki," and we mean three different things. This pins each one
down, shows how they sit on top of each other, and lays out a build order where
**you build the back-end presentation once** and then we **pour content into it
step by step** — using the Google Drive integration on `CC Blues Archive V2` as the
single physical bus that all three share.

The one-line version (corrected 2026-07-08 per Mr. Read):

> There is **one private foundation** (~100x denser, for your eyes only) and **two
> public renders of the same entries**: **the Archive** (a significantly-better-than-
> Wikipedia text encyclopedia) and **the Experience** (the same entries with visuals,
> in-browser, game-like — title pending). The foundation feeds both. `ccblues.com` is
> the POC ancestor of both.

The foundation still contains what earlier drafts called "the Wiki" (the LLM synthesis
layer) plus the Vault, the Sources, the Master DB, and the research reports. The Archive
and the Experience are **twins from one womb** — one entry schema, two skins.

---

## 1. What we made yesterday (2026-07-07 → early 07-08)

Yesterday was a **GD-19 "atlas" pass** plus the **Rent Party 11 wiki pour**. Concretely, in Drive:

- **Rent Party 11 — "the wiki pour"** (`CC Blues Vault/00-Inbox/_rent_party_11_wiki_pour_2026-07-07/`).
  11 parallel lanes (5 Cursor, 3 Antigravity, 3 Codex) poured **seed pages** into
  `_returns/` namespaces. Status now: **returned: yes, merged: yes** — Hammer merged
  them into `CC Blues Wiki/`. (`file_count: 1281` at close.)
- **A GD-19 self-map ("atlas") was generated and merged into `CC Blues Wiki/`.**
  It created a page for **every "estate place" on the map** — one page per zone/root —
  plus a scripts census and campaign logs. Two mirrored trees exist:
  - **Staging (the return):** `.../GD-19/{atlas, scripts, campaigns}` — created ~02:29 UTC.
  - **Canonical (merged):** `CC Blues Wiki/{atlas, scripts, campaigns}` — created ~02:58 UTC (the Hammer merge).
- **`atlas/`** — the place-pages: `the-wiki.md`, `archive-zone-01..09/99`, `cc-blues-db.md`,
  `cc-blues-vault.md`, `cc-blues-sources.md`, `cc-blues-poc.md`, `cc-blues-staging.md`,
  `cc-blues-journey-build.md`, `cc-blues-project-drive.md`, `cc-blues-archive-collaboration.md`,
  `archive-zone-09-cc-hub.md`.
- **`scripts/`** — the machinery census: `registry.md` (**198 scripts**: 79 LIVE, 22 DEAD, 97 UNKNOWN),
  `graveyard.md`, `_script_inventory.json`, `_build_gd19.py`, and the wiki-tooling pages
  (`wiki-index`, `wiki-log`, `wiki-lint`, `wiki-common`, `wiki-search`, `wiki-export-starter`).
- **`campaigns/`** — campaign history pages: `rent-party-11-wiki-pour-2026-07-07.md`,
  `rail-v2-frontend-wiki-campaign-2026-06-23.md`.
- **Integrity artifacts:** `contradictions-found.md`, `link_inventory.csv`, `sources.csv`.
- **The wiki toolchain is registered LIVE** in `CC Blues Wiki/_tools/`:
  - `wiki_index.py` — regenerates `index.md` + `search_index.json` (has a `--check` staleness gate).
  - `wiki_log.py` — appends `ingest|query|lint|merge` lines to `log.md`.
  - `wiki_lint.py`, `wiki_common.py` (defines `FINAL_ROOT` — the "final CC Blues Wiki home").

**Net:** yesterday we finished wiring the **Wiki's nervous system** — it can now index
itself, log operations, lint, and it holds a merged map of the whole estate plus a
census of every script. The synthesis content (artists/broadcasts/concepts) got a fresh
seed pour. What is *not* yet built is the **front-facing Archive** and the **Experience**
presentation on top of it. That is the rest of this doc.

---

## 1b. Where the information comes from — the six source layers

The private foundation is not one thing; it is a refinement stack. Rawest → most refined:

| # | Layer | Where | Scale | What it is |
|---|-------|-------|-------|-----------|
| ① | **Scholarly PDFs** | `CC Blues Archive/03 — Scholarly Sources` (+ `CC Blues Sources/pdfs`) | **39,448** files (`_parsed` 24,977, `_timelines` 13,803); 112 raw PDFs | The immutable bedrock. Paul Oliver *Aspects of the Blues Tradition*, Harry Smith *Anthology of American Folk Music*, Strachwitz *American Folk Music Occasional* 1 & 2, Wald, Lomax. |
| ② | **Primary & personal** | `CC Blues Sources` | **8,904** files | `passages/` (2,521 quotable atoms), `passage_dossiers/` (322), `notebook/` (431 scans), `narrations/` (154), `extracted_text/` (391), `lyrics/`, `counter_critics/`. |
| ③ | **AI deep research** | `CC Blues Archive/04 — Research Reports` | 234 files | Gemini Deep Research (127, **canon** per `_canon/2026-06-07_LOMAX_EQUALS_GEMINI_CANON.md`), GPT PDF Sourcing (18), Recording-Dates campaign (53), Perplexity, Wald, Influence Chains, Floating Verse. |
| ④ | **Show research** | `CC Blues Archive/02 — Show Research` | 253 files | Per-show dispatches, subtheme CSVs, Pete enrichments → vault show pages (`show_001/show_overview.md`). |
| ⑤ | **Structured spine** | `CC Blues Archive/01 — Master Database` | River/Rail/Record/Road workbooks | **You write this.** Roster, shows, tracks, stories. Agents read export copies only. |
| ⑥ | **Editorial entity graph** | `CC Blues Vault` | **75,374** files | Obsidian typed-entity wiki: `05-Artists` (1,174), `06-Shows` (4,379), `07-Stories`, `08-Influences` (296), `09-References`, `10-FloatingVerses`, `_canon/` law. The LLM Wiki synthesizes *from* here. |

**Provenance discipline already in place:** `sources:` frontmatter on every page,
`[NEEDS SOURCE]` markers, `contradictions-found.md`, `_citations/`,
`Copyright and Provenance/`, and `_canon/` rulings. This is what lets a public
"better-than-Wikipedia" entry cite itself down to the passage.

**The LLM synthesis Wiki** (`CC Blues Wiki/`, ~1,234 files: `artists/` 163,
`broadcasts/` 78, `concepts/` 120, plus `atlas/ scripts/ campaigns/`) sits at the **top**
of this stack — it is the distilled, cross-linked read of layers ①–⑥, and it is the
direct feedstock the two public renders should generate from.

---

## 2. The three things, made very clear

### 2.1 The Wiki — the local / LLM wiki (the brain)

- **Where:** `CC Blues Archive V2 / CC Blues Wiki/` — `FINAL_ROOT`. ~1,234 files.
- **What:** the **LLM-maintained synthesis knowledge base**. `artists/` (163),
  `broadcasts/` (78), `concepts/` (120), `minds/` (6), `law/` (4), plus `_data/` (400),
  `_tools/` (8), `_reports/` (7), and the roots `index.md`, `contradictions.md`,
  `open-questions.md`, `log.md`, and the new `atlas/ scripts/ campaigns/`.
- **Who writes it:** **agents.** Rent-party lanes pour seed pages into `_returns/`;
  Hammer merges into `CC Blues Wiki/`. Every page carries frontmatter
  (`title, type, slug, aliases, status, lane, sources, updated`) and `[[wikilinks]]`.
- **Audience:** **machines and us, internally.** It is a reasoning surface — dense,
  cross-linked, source-tracked, honest about `[NEEDS SOURCE]` and contradictions.
- **Job:** be the **single source of synthesized truth**. Not pretty. Correct and connected.

### 2.2 The Archive — the front-facing CC Blues Archive (the record)

- **Where:** `CC Blues Archive V2 / CC Blues Archive/` — the numbered zones:
  `01 Master Database`, `02 Show Research`, `03 Scholarly Sources`, `04 Research Reports`,
  `05 Site Design`, `06 Notebook Transcriptions`, `07 Handoffs`, `08 Scripts and Tools`,
  `09 CC Hub`, `99 Old Versions`.
- **What:** the **canonical, curated, human-facing record.** Zone 01 (Master Database)
  is **Mr. Read's Excel edit surface** — River / Rail / Record / Road. The rule is
  explicit: **"Agents read; Mr. Read writes."** and **"DO NOT TOUCH spreadsheets
  programmatically — pipeline reads export copies only."**
- **Who writes it:** **you.** This is where authorship and curation live. Agents draft
  into the Wiki; you promote what is true and finished into the Archive.
- **Audience:** **the public / the reader** — the polished front door.
- **Job:** be the **published presentation of what is verified.** The Wiki proposes;
  the Archive publishes.

### 2.3 The Experience — the CC Blues world (the whole spatial map)

- **What:** the **entire spatially-aware map and all the sub-worlds** — the estate as a
  place you move through, not a folder you open. Every zone is already modeled as an
  **"estate place on the CC Blues Archive map."** It includes the **rail-yard view**
  (`yard.html` — "the clickable rail-yard big-picture view, generated from the promoted
  DB"), the **River / Rail / Record / Road** worlds, and the RP10 display wiki / rail-v2
  frontend work.
- **Who builds it:** **you build the back-end presentation** (the map, the rails, the
  sub-world shells); content **trickles in** from the Archive.
- **Audience:** **the visitor** — someone who wants to *walk* CC Blues.
- **Job:** be the **spatial, navigable rendering** of the Archive. It shows; it does not store.

### 2.4 Side by side

| | **The Foundation** (private) | **The Archive** (public) | **The Experience** (public) |
|---|---|---|---|
| Metaphor | The bedrock + the brain | The encyclopedia | The world you walk |
| Home | `CC Blues Wiki/` + Vault + Sources + Master DB + Reports | generated public site (Archive successor of the POC) | generated public site (visual/game twin) |
| Entities | everything, ~100x denser, cited to passage | shows, artists, circles, scenes, records, reading, timelines | the **same** set, rendered spatially/visually |
| Written by | Agents synthesize; **you** write the Master DB spine | generated from the foundation | generated from the foundation |
| Read by | **you only** | the public | the public |
| Form | Markdown + `search_index.json` + spreadsheets + PDFs | text-first entries ("better than Wikipedia") | visuals + in-browser interaction |
| Role | **the source for both public renders** | reads the world | walks the world |

The flow is **one foundation → two twin renders**: `Foundation → { Archive, Experience }`.
The Archive and the Experience are the same entries with different skins; neither authors
data, both generate from the foundation. Nothing public is authored directly.

---

## 3. The integration model — one substrate, one foundation, two renders

Everything shares **one physical substrate: `CC Blues Archive V2` on Google Drive.**
That is the whole point of the Google Drive integration — it is the **bus** the foundation
and both public renders talk over, so we never build a parallel store.

```
   SOURCE LAYERS ①–⑥  (PDFs · passages · deep research · show research · Master DB · Vault)
                          │  agents synthesize; you write the Master DB spine
                          ▼
                 THE LLM WIKI  (CC Blues Wiki/ — distilled, cited, cross-linked)
                          │  wiki_index.py → search_index.json
                          ▼
              ┌───  THE ENTRY SCHEMA  ───┐     ← the one back-end presentation you own
              │   (one entry format,     │
              │    two renderers)        │
              ▼                          ▼
      (A) THE ARCHIVE            (B) THE EXPERIENCE
       text encyclopedia          same entries + visuals, in-browser
       (public website)           (public, game-like, title pending)
              └──────── ccblues.com POC is the shared ancestor of both ────────┘
```

**Google Drive is the integration layer, doing three concrete jobs:**

1. **Read bus.** Agents and generators read Archive V2 (Master DB export copies, Vault
   editorial, Wiki pages) directly over the Drive integration — the same way this session
   read the atlas. No copy-down, no drift.
2. **Write bus / staging.** Agent output lands in `_returns/` (rent-party pattern) or a
   `00-Inbox/` campaign folder; a **merge step** ("Hammer") promotes into the canonical
   home. This is already how RP11 worked.
3. **Presentation source.** Both public renders are **generated from** the foundation —
   the `cc-blues-poc` build already proves this (`build_lean_site.py` → lean `data/` →
   static `site/` on Netlify, with per-show pages and cover art). The Archive and the
   Experience are its grown-up successors, reading the same source.

---

## 4. How to complete each — complementary, step by step

Design principle you set: **you build the back-end presentation of everything first**
(the one entry schema both renders share), **then we trickle content piece by piece.**

### Track 0 — Harden the foundation — _mostly wired as of yesterday; needs discipline_

1. **Lock the Wiki tool loop.** Make `wiki_index.py --check`, `wiki_lint.py`, `wiki_log.py`
   the required close-out of every pour.
2. **Resolve `contradictions-found.md` / `open-questions.md`** into facts or explicit
   `[NEEDS SOURCE]` holds.
3. **Triage `registry.md`** (97 UNKNOWN scripts → LIVE/DEAD; DEAD to `graveyard.md`).
4. **Standardize frontmatter + `sources:`** so `search_index.json` is complete and every
   claim is cited to a source layer (①–⑥). This JSON is what both renders read.

### Track 1 — The entry schema — _the one back-end presentation you own (do this first)_

1. **Design one entry format** covering all public entity types: **shows, artists, circles,
   scenes, records, reading content, timelines** (+ more). One schema → two renderers.
2. **Decide the render split:** the Archive consumes the entry as **text-first HTML**; the
   Experience consumes the **same entry** as a visual/interactive node. Same data, two skins.
3. **Set the promotion gate** (see §5 decision B): recommend **auto-draft, you release** —
   verified entries auto-stage as unpublished drafts; you flip batches live.

### Track 2 — The Archive (public text encyclopedia) — _prove the pipe on one entry_

1. Take **one artist** fully end-to-end: foundation → entry → published Archive page.
   Artists first — most fuel (163 Wiki + 1,174 Vault artist files) and the clearest place
   to beat Wikipedia (passages, narrations, citation dossiers they lack).
2. Then repeat across the roster → Shows → Records/Timelines. No new architecture per type.

### Track 3 — The Experience (public visual/game twin) — _same entries, visual skin_

1. Point the **visual renderer** at the exact same entry the Archive uses; render the one
   proven artist as a visual/interactive node (build on `cc-blues-poc` covers + the rail views).
2. Grow the spatial map (River/Rail/Record/Road) as entries go live — it fills automatically
   as Track 2 advances, because it authors nothing.

### The complementary loop

```
Agents synthesize → Wiki (Track 0) → entry schema (Track 1) → you release verified drafts
        ▲                                        │
        │                                        ├──► Archive page   (Track 2, text)
        │                                        └──► Experience node (Track 3, visual)
        └────  gaps either render exposes become open-questions back in the Wiki  ────┘
```

Build order: **Track 0 is essentially done** (harden it) → **Track 1 is the real work you
own** (one entry schema + promotion gate) → **Tracks 2 & 3 are twin renderers** that get
cheap once the schema exists. Everything rides the Google Drive integration on
`CC Blues Archive V2`; nothing needs a second store.

---

## 5. Decisions — talked through (2026-07-08)

- **A. Archive form → published website.** Confirmed by Mr. Read: the only public text is a
  significantly-better-than-Wikipedia encyclopedia. The Experience is its visual twin. Both
  generate from one entry schema. (Not curated Drive pages.)
- **B. Promotion gate → recommend "auto-draft, you release."** Verified entries auto-stage
  as drafts; you flip them live in batches. Keeps your editorial veto without mechanical work.
  _(Open for your call: manual-only vs. auto-on-verified vs. auto-draft.)_
- **C. First entity → Artists (River).** Most fuel and the clearest "better than Wikipedia"
  win. Prove the full pipe on one artist, then repeat.

## 6. Blockers & immediate next moves

1. **`ccblues.com` is unreachable from this environment** — the network policy denies the
   connection at the proxy (`connect_rejected`, gateway 403). To let me study the live POC,
   add `ccblues.com` to the environment's allowed domains (Claude Code on the web settings:
   https://code.claude.com/docs/en/claude-code-on-the-web). I learned the POC's shape from
   Drive regardless (`cc-blues-poc`: lean static site, Netlify, per-show pages + covers).
2. **Design the one entry schema** (Track 1) — everything downstream keys off it.
3. **Confirm decision B** (the promotion gate) so the generator knows its publish trigger.
4. **Decide where the working scribe/spec lives in Drive** — `CC Blues Vault/00-Inbox/` as a
   new campaign (matches the rent-party pattern), or `CC Blues Wiki/` root.

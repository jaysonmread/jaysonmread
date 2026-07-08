# CC Blues — Wiki, Archive, Experience: the three things, and how they complete each other

_Scribed 2026-07-08. Substrate: `My Drive / CC Blues Archive V2`. Author builds the back-end presentation; content trickles in piece by piece._

---

## 0. Why this doc exists

We keep saying "the wiki," and we mean three different things. This pins each one
down, shows how they sit on top of each other, and lays out a build order where
**you build the back-end presentation once** and then we **pour content into it
step by step** — using the Google Drive integration on `CC Blues Archive V2` as the
single physical bus that all three share.

The one-line version:

> **The Wiki** is the brain. **The Archive** is the record. **The Experience** is the world.
> The Wiki knows, the Archive holds, the Experience shows.

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

| | **The Wiki** | **The Archive** | **The Experience** |
|---|---|---|---|
| Metaphor | The brain | The record | The world |
| Path / home | `CC Blues Wiki/` (`FINAL_ROOT`) | `CC Blues Archive/` (zones 01–99) | `yard.html` + sub-worlds (rendered) |
| Written by | Agents (rent-party → Hammer merge) | **You** (curate/promote) | You (shell) + trickle from Archive |
| Read by | Machines + us | The public | The visitor |
| Form | Markdown + `search_index.json`, wikilinks | Curated pages, spreadsheets, exports | Spatial map, rails, sub-worlds |
| Truth role | Proposes / synthesizes | **Publishes / canonizes** | Renders / presents |
| Editable how | Automated, high-churn | Deliberate, low-churn, human | Generated from Archive/DB |

The flow is a one-way ratchet: **Wiki → Archive → Experience.** Nothing skips a layer.

---

## 3. The integration model — one substrate, three layers

Everything shares **one physical substrate: `CC Blues Archive V2` on Google Drive.**
That is the whole point of the Google Drive integration — it is the **bus** the three
layers talk over, so we never build a parallel store.

```
                MASTER DATABASE (you write, Excel)          ← Zone 01 River/Rail/Record/Road
                          │  export copies only
                          ▼
                 cc-blues-db  (promoted DB / working_index.assembly.sqlite)
                          │
        ┌─────────────────┼──────────────────────────┐
        ▼                 ▼                           ▼
  (1) THE WIKI       search_index.json          yard.html generator
  agents synthesize   (wiki_index.py)           (spatial render)
        │                                            │
        │ you promote verified entries               │ trickle content
        ▼                                            ▼
  (2) THE ARCHIVE  ──────────────────────────►  (3) THE EXPERIENCE
   canonical record        renders as              spatial world / sub-worlds
```

**Google Drive is the integration layer, doing three concrete jobs:**

1. **Read bus.** Agents and generators read Archive V2 (Master DB export copies, Vault
   editorial, Wiki pages) directly over the Drive integration — the same way this session
   read the atlas. No copy-down, no drift.
2. **Write bus / staging.** Agent output lands in `_returns/` (rent-party pattern) or a
   `00-Inbox/` campaign folder; a **merge step** ("Hammer") promotes into the canonical
   home. This is already how RP11 worked.
3. **Presentation source.** The back-end presentation (Experience) is **generated from**
   the promoted DB and the Archive — `yard.html` already does exactly this. New sub-worlds
   read the same source, so building the shell once lets any Archive content trickle in.

---

## 4. How to complete each — complementary, step by step

Design principle you set: **you build the back-end presentation of everything first,
then we trickle content piece by piece.** So each track below is ordered *scaffold → pour*.

### Track A — Finish the Wiki (the brain) — _mostly wired; needs discipline_

1. **Lock the tool loop.** Make `wiki_index.py --check`, `wiki_lint.py`, and `wiki_log.py`
   the required close-out of every pour. (Nervous system exists as of yesterday — just enforce it.)
2. **Resolve `contradictions-found.md` and `open-questions.md`** into either Archive facts
   or explicit `[NEEDS SOURCE]` holds. Don't let them rot.
3. **Triage `registry.md`** — 97 UNKNOWN scripts. Decide LIVE/DEAD so the machinery census
   stops being noise. Move DEAD to `graveyard.md`.
4. **Standardize frontmatter + wikilinks** so `search_index.json` is complete — this JSON is
   what the Archive and Experience will query. **This is the contract; harden it first.**

### Track B — Build the front-facing Archive (the record) — _the back-end presentation you own_

1. **Define the Archive schema / template** — the canonical page shape a reader sees
   (artist, show, source, concept). **This is "the back-end presentation of everything."** Build it once.
2. **Set the promotion gate.** One rule: an entry appears in the Archive only when its Wiki
   page is `status: verified` with real `sources`. Wiki proposes → you approve → Archive publishes.
3. **Wire the trickle.** A generator reads `search_index.json` + Master DB exports and emits
   Archive pages into the template. Start with **one zone end-to-end** (suggest **01 River /
   artists** — richest, 163 wiki pages ready) to prove the pipe.
4. **Pour piece by piece.** Once one zone is real, the rest is repetition: broadcasts, then
   concepts, then sources. No new architecture per zone.

### Track C — Grow the Experience (the world) — _shell now, content trickles_

1. **Promote `yard.html` to the map shell.** It already renders the rail-yard from the
   promoted DB — make it the front door and the navigation spine for River/Rail/Record/Road.
2. **Stand up empty sub-world shells** for each world, reading the same DB/Archive source.
   Empty is fine — the point is the shell exists so content has somewhere to land.
3. **Bind Experience tiles to Archive pages.** Each spatial node links to its Archive page
   (which is backed by its Wiki page). Click a stop on the rail → the published record opens.
4. **Trickle spatial content** as Archive zones go live in Track B. Experience never authors —
   it only renders what the Archive has published, so it fills in automatically as B advances.

### The complementary loop

```
Agents pour → Wiki (Track A)  →  you verify/curate → Archive (Track B)  →  auto-renders → Experience (Track C)
     ▲                                                                                          │
     └───────────────────  gaps the Experience exposes become open-questions in the Wiki  ─────┘
```

Build order: **A is essentially done** (harden it) → **B is the real work and the part you
own (the template + promotion gate)** → **C is cheap once B produces pages** (shell + bind).
Everything rides the Google Drive integration on `CC Blues Archive V2`; nothing needs a
second store.

---

## 5. Immediate next moves (smallest useful steps)

1. **Confirm the naming** in §2 matches how you think of them — then this doc is the shared
   vocabulary (Wiki = brain, Archive = record, Experience = world).
2. **Design the Archive page template** (Track B1) — the one back-end presentation shape.
   Everything downstream keys off it.
3. **Pick the first zone to take end-to-end** — recommend **River / artists** (163 Wiki pages
   already seeded, so the trickle has fuel).
4. **Decide where the working scribe/spec lives in Drive** — `CC Blues Vault/00-Inbox/` as a
   new campaign (matches the rent-party pattern), or `CC Blues Wiki/` root.

---

### Open questions for you

- Is the **front-facing Archive** a set of curated Drive pages, a **published website**, or
  both? (It changes whether Track B emits Markdown, HTML, or DB rows.)
- Is the **Experience** one map with sub-worlds, or separate deployables that share the map shell?
- Should the **promotion gate** (Wiki→Archive) be manual (you approve) or rule-based
  (`status: verified` auto-promotes)?

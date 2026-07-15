# CC Blues — Vision & Conceptual Model

_Consolidated from `wiki-archive-experience.md` and `experience-architecture.md`. This is the
"what are we building and why" document. 2026-07-15._

---

## 1. The subject

CC Blues is an archive of **Black American music** — the blues and the American folk
tradition around it. It is organized as a **museum-railroad**: an invented, spatially
navigable world where the history is walked, not just read. The house setting is a night
railyard in **Florence, Alabama** (near the Tennessee River / Muscle Shoals), fog, amber
lamps, no people. The blues is treated as *music moving through time, place, bodies,
machines, institutions, memory, and argument* — never as one line of "development."

## 2. The three things (keep these distinct — it is the founding clarification)

### The Foundation — private, dense, the source of everything
Mr. Read's words: "the local content, for my eyes only, is probably 100× more dense and is
used as the source for the other two." It is six source layers (detailed in
`03-drive-map-and-corpus.md` and `wiki-archive-experience.md`):
1. **Scholarly PDFs** — the immutable bedrock (Zone 03, ~39k files).
2. **Primary & personal** — passages, notebooks, narrations (CC Blues Sources, ~8.9k files).
3. **AI deep research** — internal leads only; NEVER cited publicly.
4. **Show research** — per-show dispatches, subtheme CSVs.
5. **The structured spine** — the Master Database (River/Rail/Record/Road workbooks; Mr.
   Read writes, agents read export copies only).
6. **The editorial entity graph** — the Vault (Obsidian typed entities, ~75k files).
On top of these sits **the LLM synthesis Wiki** (`CC Blues Wiki/`, the distilled, cited,
cross-linked read of layers 1–6). Everything public is generated from here.

### The Archive — public text encyclopedia ("significantly better than Wikipedia")
Text entries for **shows, artists, circles, scenes, records, reading content, timelines, and
more**. Better than Wikipedia because every source is a *positioned* document with a usage
ruling, and every claim cites a real source down to the page/passage.

### The Experience — public visual/game world (title pending)
The **same entries** as the Archive, rendered spatially and interactively — "basically the
same Wikipedia-style deal except it has visuals to go with it and it's like a video game
basically in browser." ccblues.com is the current POC ancestor (a lean static site;
`build_lean_site.py` → Netlify; currently **egress-blocked** from this environment).

### The keystone relationship
**The Archive is the Experience's `READ MODE`.** Every world page carries a READ MODE control
that flattens the spatial scene into an accessible linear article of the same callouts +
citations. One entry → two views (spatial + linear). This collapses "build the Archive" and
"build the Experience" into a single pipeline over the entry schema.

```
   SOURCE LAYERS 1-6  →  THE LLM WIKI (foundation)  →  THE ENTRY SCHEMA  →  { Experience (spatial) , Archive (READ MODE, linear) }
```

## 3. The six worlds = six verbs (LOCKED 2026-07-10)

| World | Verb | Core question | Notes |
|---|---|---|---|
| **RAIL** | assembles | How is this history assembled into a journey? | the archive's own structure: show-trains, artist cars, Circle cars, Record cars, yard, roundhouse, Concourse |
| **RIVER** | carries | How do songs/practices/memories/influences flow through time? | continuity without a single origin; tributaries merge/vanish/reappear |
| **ROAD** | moves | Where did people/songs/instruments/labor/markets travel? | migration, touring, the automobile, the *broken* road (segregation) |
| **RECORD** | spins | What survives as sound made into things? | labels, discs, vinyl, sheet music, piano rolls, field discs; chain: performance→take→object→reissue |
| **READING** | tells | Who has told this history, and how? | ledger / witness / argument; scholarship, the Argument Wall |
| **RADIO** | transmits | What could people hear, where, placed by whom? | broadcast as listening history |

**RECORD and READING are the two "evidence worlds"** — grooves and ink. Every Receipt view
in *any* world bottoms out in a playable object (Record) or a citable page (Reading). The
other four worlds are interpretive *lenses* over that evidence.

**The Concourse** is the homepage / transfer point (the Florence depot). A suspended station
clock is a **global time control** — dragging it changes the historical period across the
whole archive. **A pinned "journey ticket"** carries one subject (an artist, song, place,
concept) through all six worlds: "the same recording has not changed; the question being
asked of it has changed." That is the central intended intellectual experience.

## 4. The shared interaction grammar (learn once, works everywhere)

1. **Four zoom levels:** Horizon → District → Artifact → **Receipt**. (Horizon culling = the
   API importance score. Receipt view = the full citation: source, claim ID, quote, evidence
   class, uncertainty, contradiction, related recordings.)
2. **Five callout types:** PLACE · PERSON · SOUND · SYSTEM · QUESTION (each a distinct glyph
   silhouette; color encodes function, not decoration).
3. **Two layers of writing:** "What happened" + "Why it matters" on top; an expandable
   **Paper Trail** (citations, qualifications, alternate claims) beneath.
4. **Persistent listening dock** across worlds.
5. **Carry a thread** (the journey ticket).

Per-page control rail: `MAP · TIME · LISTEN · THREAD · LAYERS · READ MODE · RETURN`.

## 5. The entry — the single load-bearing artifact

One file per subject. Its frontmatter is a structured record (fuels the spatial Experience);
its body is Pete-voice prose (fuels the Archive/READ MODE). It matches the **real, already-
built `carData` contract** in `car_template_v2.html`: `identity`, `stations {objects,
records, reading, circle{people,scenes}, timeline}`, `_flags`, `wiki_url`, plus `worlds[]`,
`callout_type`, `api_score`, and a promotion gate. **Every clickable element in the UI is a
schema field wearing a costume** — but clicks write only to ephemeral `ui_state`, never to
the canonical entry. Full spec: `entry-schema.md`.

## 6. Importance = the API score (not a metaphor)

"How important is this artist/event" is answered by a deterministic **A-Priori-Importance
(API) score** already built (`codex-score`): `catalog_size + co-mention degree + source
corroboration`, normalized 0–100. It powers **Degree-of-Interest culling** (zoomed out, only
landmarks render). In prose, stature is *shown then named* in Framing-Standard vocabulary
(landmark, master practitioner, innovator, architect) — never a ladder metaphor. See
`02-locked-canon.md` for the banned language.

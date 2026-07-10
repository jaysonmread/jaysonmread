# CC Blues — Handoff Brief: State of the Architecture + the Interface Assignment

_For ChatGPT — same thread as your "Six Ways the Blues Moves" memo and image-campaign
review. Prepared 2026-07-10 by Mr. Read with Claude. You have Google Drive access; a
reading list is in §7. Read this brief first, then the Drive files, then respond to the
assignment in §5._

---

## 1. What we adopted from your memo (now locked)

Your review landed. The following are canon as of this week:

- **Six worlds** — RAIL · RIVER · ROAD · RECORD · READING · RADIO — joined at the Concourse
  (Florence depot at night), with the suspended station clock as global time control and the
  pinned **journey ticket** carrying one subject through all six.
- **The Archive is the Experience's READ MODE.** The "significantly better than Wikipedia"
  public encyclopedia and the navigable world are one build, two views: spatial and linear.
  Every world page's READ MODE flattens its callouts + citations into an accessible article.
- **The shared interaction grammar**: four zoom levels (Horizon → District → Artifact →
  Receipt), five callout types (PLACE · PERSON · SOUND · SYSTEM · QUESTION, each with its own
  marker shape; color = function), two-layer writing (What happened / Why it matters +
  expandable Paper Trail), persistent listening dock, carry-a-thread.
- **The per-page control rail**: MAP · TIME · LISTEN · THREAD · LAYERS · READ MODE · RETURN.
- **The image-text law**: generated lettering is placeholder texture only; every factual
  title, date, number, and citation is overlaid deterministically from the canonical
  database. Real archival photographs in standardized empty windows; **no generated faces,
  no AI-written factual copy, ever.**
- **Three visual registers**: A (living world, saturated chromolithograph), B (railroad
  archive at night), C (documentary evidence). Night register B stops doing every job.
- **Edit, don't invent**: freeze broad generation → rule ~30 canonical winners → re-render
  at production sizes → complete the archival-photo pipeline → build Show 001 as the
  gold-standard vertical slice.

## 2. Decisions made since your memo (the deltas)

1. **The six verbs are finalized**, with two corrections to your draft:
   **RAIL assembles · RIVER carries · ROAD moves · RECORD spins · READING tells · RADIO
   transmits.**
   - "RECORD fixes" was rejected: "fix" reads as *repair* (colliding with the Repair Track),
     and a verb that needs a footnote fails the democratic register. "Keeps" was also
     rejected — keeping is what Record and Reading share (they are the two evidence worlds),
     so it cannot name either one. **"Spins"** names Record's distinctive power in the
     music's own vernacular.
   - "READING interprets" was rejected as over-claiming: much of Reading merely states facts.
     Reading has **three registers of ink** — the **ledger** (discographies, session logs,
     catalogs: tells you *what*), the **witness** (memoirs, interviews, oral histories: tells
     you *how it was*), and the **argument** (criticism, scholarship: tells you *what it
     means*). The honest umbrella across all three: **"tells."**
2. **The Record world charter**: Record is the world of **sound made into things** — labels,
   discs, vinyl, the whole commercial and material life of recorded sound, including the
   pre-phonograph objects (sheet music, piano rolls — the 1912 published blues preceded the
   1920 first blues disc) and non-commercial sound objects (field discs, test pressings,
   unissued takes). Its internal chain: **performance → take/matrix → issued object →
   reissue.**
3. **The performance principle (anti-survivorship-bias, Mr. Read's ruling)**: performances
   are **events**, never Record objects — even when a recording of them exists. Most blues
   performances left no object; if performances lived inside Record, the architecture would
   quietly claim only recorded music happened. Events may link to surviving artifacts
   (`survives_as`), objects link back to the event they document — but they never merge.
4. **Sheet music sits on the fork deliberately**: it is ink that encodes sound — a Record
   object by commerce, Reading material by nature. It gets dual world membership rather than
   a forced home. (Boundary test: can it make the music sound again without someone reading
   words? Disc yes, piano roll yes, sheet music no.)
5. **Citation integrity is structural law**: public citations come only from real sources
   (scholarly / primary / periodical / liner / archive / discography / reference).
   Deep-research reports, Wikipedia harvests, and anything AI-generated live in a private
   `_leads` field — used to *locate* real footnotes, never rendered, never cited. `[DR-GAP]`
   blocks publication. The word "AI" never appears in public output.
6. **Importance is the API score** (the deterministic A-Priori-Importance / Degree-of-Interest
   system already built: catalog size + co-mention degree + source corroboration). It drives
   Horizon-view culling. In prose, stature is *shown then named* in Framing-Standard
   vocabulary (landmark, master practitioner, innovator, architect) — never ladder metaphors.
7. **The entry schema** (one file per subject) is the single contract both views render
   from. Its Rail face matches the existing `car_template_v2.html` carData contract exactly:
   `identity`, `stations: { objects, records, reading, circle: {people, scenes}, timeline }`,
   `_flags`, `wiki_url`. Added since: `worlds: []` (multi-world membership),
   `callout_type`, QUESTION as a first-class entry type, `api_score`, and the
   promotion gate (`status` → `published`, flipped by Mr. Read in batches).

## 3. The production pipeline (decided)

- **ChatGPT + Midjourney = the audition instrument.** Prompt packets → exploratory
  generations → the visual sketchbook. This is where the world gets *discovered*. (It is how
  everything so far was made, and it stays.)
- **ComfyUI = the production instrument.** Winners get formalized into deterministic,
  reusable assets: seeded and repeatable workflows, batch size variants (16:9 hero, 3:1
  banner, 4:5 card, 1:1 tile, 9:16 mobile), inpaint-cleared text-safe zones, blank-text
  versions, archival photographs composited into the empty portrait windows, style held
  consistent by reference workflows built from the ruled winners.
- **Three asset classes route differently:**
  1. **Scene art** (world heroes, car exteriors as illustration) — raster; Midjourney →
     ComfyUI; registers A/B.
  2. **Interface objects** (dials, markers, tickets, switches, glyphs, the control rail) —
     Midjourney *auditions the style only*; finals are **redrawn as SVG/code** so they scale,
     recolor per world, and carry real text. (The existing car template's pure-CSS Pullman
     exterior is the proof this works.)
  3. **Evidence material** (archival photos, documents, real typography) — never generated,
     only composited; register C.

## 4. The governing discipline (unchanged, applies to everything you propose)

The Framing Standard governs all public-facing language and organization: name the maker,
the music, the musical action, the evidence, the money when it matters; no "discovered," no
evolutionary ladders, no vibe-as-evidence; the four functional-aesthetic yard nodes are the
primary navigation with region demoted to a facet; the Circle surfaces authorship, credit,
and economics without making mediators the protagonists. Uncertainty is public and
first-class (the Repair Track, the Argument Wall, QUESTION callouts).

## 5. YOUR ASSIGNMENT: the visible & clickable element system

Design the complete **interactive element inventory** for the site — everything a visitor
can see, click, drag, tune, flip, pin, or expand — as a formal component system. Give us
your own interpretation; disagree where you see better structure. We are organizing our
thinking in **seven families**; use, amend, or argue with them:

1. **Persistent chrome** (every page): control rail, audio dock, journey ticket, Concourse
   return.
2. **Navigational instruments** (world level): departure board, station clock, minimap,
   LAYERS toggles, world-to-world crossings.
3. **Entry surfaces** (subject level): car exterior/door, the five in-car stations,
   plaques, portrait windows.
4. **Callout markers**: the five types as a glyph system — distinct silhouette per type,
   legible at map scale and at mobile size.
5. **Evidence controls**: Paper Trail expander, receipt chip, corroboration badge,
   evidence-class icons (ledger / witness / argument for Reading sources; sound-object for
   Record sources).
6. **World-signature interactions** (one per world): Rail yard switch (multi-track
   membership) · River song-token release · Road two-place route query · Record disc flip
   (Listen / Session / Object / Circulation / Evidence / Afterlife) · Reading comparison
   table · Radio tunable dial (city / date / station / signal reach).
7. **State indicators**: Repair-Track badges, DR-GAP, api-tier prominence, published/draft,
   under-construction.

**For every element, specify:**
- What it looks like (and which visual register A/B/C it belongs to)
- What clicking/dragging it does — and **which entry-schema field it reads or writes**
  (the discipline: every clickable is a schema field wearing a costume; no clickable without
  a field, no field unreachable by click)
- Which asset class (scene raster / vector-code interface object / composited evidence)
- Text-safe and real-typography requirements
- Mobile behavior (the review's own warning: at phone size, warm rectangles and glowing
  windows — distinctions must survive the small screen)
- Accessibility fallback (everything must survive READ MODE linearization)

**Also deliver:**
- **The schema→click mapping table** — one row per interactive element, mapping it to the
  carData / entry field it renders. This table is the contract between design and data.
- **A glyph brief** for the marker/icon system (five callouts + evidence classes + control
  rail), written as a Midjourney audition packet (style exploration only, no factual text)
  with the explicit note that finals will be redrawn as SVG.
- **A Midjourney campaign packet structure for interface objects** — like PACKET_artist_05
  but for tickets, dials, switches, boards: blank signboards, large text-safe areas, single
  objects on neutral grounds, register-locked palettes.
- **ComfyUI production workflow recommendations** — how you'd structure the
  audition-winner → deterministic-asset conversion (reference/style consistency, size
  matrix, blank-text + typography-overlay variants, photo compositing steps).
- **A first build list**: the ~15 elements you would build first to make the Show 001
  gold-standard slice and one artist car (Lead Belly) fully clickable.

## 6. Non-negotiable constraints (verbatim summary)

No AI-generated factual typography. No generated historical likenesses — real archival
photographs in empty windows only. Framing-Standard language everywhere public. Color
communicates function. Diegetic-first UI (objects of the world, not floating widgets) with
READ MODE as the accessibility guarantee. Uncertainty rendered, not hidden. Everything
public cites real sources only.

## 7. Google Drive reading list (search these filenames)

Get up to speed by locating and reading (Drive search by filename; all under
`CC Blues Archive V2/`):

- `2026-06-17_FRAMING_STANDARD_BLACK_AMERICAN_MUSIC.md` — the language/organization canon
- `2026-05-22_TRAIN_DEPOT_ARCHITECTURE.md` — the depot/yard architecture canon
- `car_template_v2.html` — the working artist-car prototype (carData contract, stations,
  door interaction, day/night mode) — **read the JS: the summary builders define the data
  contract**
- `2026-06-12_MATRIX_V2_PLAN.md` — the image-campaign audition/ruling plan
- `PACKET_artist_05.md` — the rail-car contact-sheet prompt packet (register B lock)
- `codex-score_importance_DOI.md` + `artist_importance.csv` / `event_importance.csv` — the
  API importance system
- `River_and_Blues_Source_Reader.md` / `Road_and_Blues_Source_Reader.md` — the River/Road
  research beds
- `SCN-groves.md` — the radio world (Airwave Groves) concept
- `registry.md` (GD-19 scripts) and `the-wiki.md` — the foundation's self-map, if useful

## 8. What to return

A single markdown document: your interpretation of the element system (families, inventory,
per-element specs), the schema→click mapping table, the glyph brief, the interface-object
Midjourney packet, the ComfyUI workflow plan, and the Show-001 + Lead Belly first-build
list. Where you disagree with anything in §2–§5, say so directly and propose the alternative
— the disagreements are the valuable part.

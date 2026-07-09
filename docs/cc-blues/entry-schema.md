# CC Blues — the Entry Schema (v0.1 draft)

_One entry format, two public renderers. The frontmatter is the structured record
(fuels the visual **Experience**); the body is the prose (fuels the text **Archive**).
Every claim cites back to the six source layers. Drafted 2026-07-08 for Mr. Read's approval._

---

## 0. The one rule

> **One self-contained file per entry.** Its **frontmatter is the data record**; its
> **body is the encyclopedia prose**; its **`sources:` block is the citation ledger.**
> The Archive renders the prose + a facts sidebar + references. The Experience renders the
> same file as a node on the map. Neither renderer stores anything the entry file doesn't.

```
                       one entry file (.md)
                       ┌───────────────────┐
   structured record → │  --- frontmatter ---   → visual face  → THE EXPERIENCE (node/map/timeline)
   citation ledger   → │  sources: [...]     │
   encyclopedia prose→ │  # Body (prose)     │   → text face    → THE ARCHIVE (article + refs)
                       └───────────────────┘
```

---

## 1. Shared core (every entry, all types)

```yaml
---
# identity
id: lead-belly                 # stable slug; never changes; the public URL key
type: artist                   # artist | show | circle | scene | record | reading | timeline | track | place | story
title: "Lead Belly"
display_name: "Huddie William Ledbetter"
aliases: ["Leadbelly", "Huddie Ledbetter"]
summary: "Twelve-string songster whose repertoire became a spine of the American folk revival."   # one line; card/tile text

# lifecycle & the promotion gate  (decision B: auto-draft, you release)
status: verified               # seed → draft → verified → published
visibility: public             # private | public
published: false               # true only when YOU flip it live (batch release)
updated: 2026-07-08

# spatial placement  (the Experience)
world: River                   # River | Rail | Record | Road
map:
  node: river/songsters/lead-belly
  coords: [x, y]               # or leave null to auto-layout
timeline:
  span: [1888, 1949]           # single date or [start, end]

# media  (the Experience; optional in the Archive sidebar)
media:
  hero: covers/artists/lead-belly.jpg
  gallery: [ ... ]
  audio: [ { title: "Goodnight Irene", ref: record:goodnight-irene } ]

# relations  (typed links; power the Experience's influence lines & the Archive's "see also")
relations:
  - { rel: member_of,     ref: circle:lomax-circle }
  - { rel: performed_in,  ref: scene:new-york-folk-revival }
  - { rel: influenced,    ref: artist:woody-guthrie }
  - { rel: recorded,      ref: record:goodnight-irene }

# citation ledger  → every source layer ①–⑥ (see §3)
sources:
  - { key: oliver-aspects,  layer: 1, path: "03 — Scholarly Sources/aspectsofbluestpauloliver.pdf", locator: "pp.112–118" }
  - { key: songster-strand, layer: 6, path: "CC Blues Vault/05-Artists/lead-belly/…", note: "songster-archive strand" }
  - { key: gemini-dr-leadbelly, layer: 3, path: "04 — Research Reports/Gemini Deep Research/…", note: "canon per LOMAX_EQUALS_GEMINI" }
---
```

**Field notes**
- `status`/`visibility`/`published` = the **promotion gate**. When the foundation marks an
  entry `status: verified`, the generator stages it `visibility: public, published: false`
  (a draft on the public site, unlisted). **You flip `published: true` in batches.**
- `world` + `map` = where it sits in the spatial Experience. `River/Rail/Record/Road` are the
  existing Master-DB worlds; the map node id is stable so links never break.
- `relations` are **typed** so the Experience can draw the right kind of line (influence vs.
  membership vs. performance) and the Archive can group "See also" correctly.
- `sources[].layer` ties each citation to one of the six source layers, so provenance is
  machine-checkable — this is the "better than Wikipedia" guarantee.

---

## 2. Per-type extension blocks

Each `type` adds a small typed block under the core. Only the deltas are shown.

**artist**
```yaml
born: { date: 1888, place: "Mooringsport, Louisiana" }
died: { date: 1949, place: "New York City" }
instruments: ["twelve-string guitar", "vocals", "accordion"]
active_years: [1900, 1949]
circles: [circle:lomax-circle]
scenes:  [scene:new-york-folk-revival]
notable_records: [record:goodnight-irene]
```

**show**  (a CC Blues broadcast/episode)
```yaml
number: 1
air_date: 2026-01-15
theme: "…"
subthemes: [ ... ]          # from Zone 02 subthemes.csv
setlist: [ track:…, track:… ]
featured_artists: [ artist:… ]
```

**circle**  (a social/collaborative grouping — people who worked together)
```yaml
members: [ artist:…, artist:… ]
time_span: [start, end]
place: "…"
defining_relationship: "…"  # what makes it a circle
```

**scene**  (a geographic-temporal grouping — a place-and-era sound)
```yaml
place: "…"
era: [start, end]
artists: [ artist:… ]
venues: [ place:… ]
defining_sound: "…"
```

**record**  (a release/recording)
```yaml
artist: artist:lead-belly
label: "…"
recording_date: …
release_date: …
format: "78rpm | LP | field recording"
tracks: [ track:… ]
```

**reading**  (public-facing "reading content" — a curated pointer into the scholarship)
```yaml
work_title: "Aspects of the Blues Tradition"
author: "Paul Oliver"
year: 1970
source_layer: 1
key_passages: [ passage:… ]  # from CC Blues Sources/passages
relevance: "…"
```

**timeline**  (a rendered span; the Experience draws it, the Archive lists it)
```yaml
span: [start, end]
events:
  - { date: …, ref: artist:…, note: "…" }
  - { date: …, ref: record:…, note: "…" }
```

---

## 3. The citation model (why this beats Wikipedia)

Every prose claim in the body carries an inline marker that resolves to a `sources[]` key:

```markdown
Ledbetter's twelve-string technique anchored a repertoire that Alan Lomax would later
frame as a national songbook.{cite:oliver-aspects} His "Goodnight Irene" became the
revival's signature.{cite:gemini-dr-leadbelly}
```

- `{cite:KEY}` → looks up `sources[KEY]` → renders a footnote in the Archive with the
  **layer, path, and locator** (page/passage). The Experience shows the same as a hoverable
  provenance chip.
- Because `layer` is explicit, we can **enforce**: no claim publishes without a citation
  into layers ①–⑥, and any `[NEEDS SOURCE]` marker blocks `published: true`.
- Source layers (recap): ① Scholarly PDFs · ② Primary/passages · ③ AI deep research
  (Gemini = canon) · ④ Show research · ⑤ Master DB spine · ⑥ Vault editorial graph.

---

## 4. How the two renderers consume one entry

| Frontmatter/body element | Archive (text) | Experience (visual) |
|---|---|---|
| `summary` | lede / card | tile label + hover |
| body prose + `{cite:}` | the article + footnotes | expandable panel |
| `sources[]` | References section | provenance chips |
| `relations[]` | "See also" list | drawn lines between nodes |
| `world` + `map` | breadcrumb | node placement on the map |
| `timeline` | dates in infobox | plotted on the timeline rail |
| `media` | inline images | hero art, audio, gallery |
| `status/published` | omit if not published | omit if not published |

**Both read the identical file.** Building one entry correctly means both public renders of
it exist for free — which is exactly the "twin renders of the same entries" model.

---

## 5. Worked example status & next action

- The Lead Belly frontmatter above is **illustrative scaffolding** — real values (dates,
  places, `sources` paths) get filled and **verified against the corpus** when we build the
  first real entry. Nothing here is published truth yet.
- **Next action:** once Drive is reconnected, confirm the richest first artist (Lead Belly or
  another), then build **one fully-sourced entry** end-to-end to stress-test this schema
  before we scale. Any field that fights the first real artist gets fixed here in v0.2.

### Open for your call
1. `{cite:KEY}` inline marker syntax — fine, or prefer a different token?
2. `world` values — keep River/Rail/Record/Road, or add worlds for circles/scenes/reading?
3. Promotion gate default (`published: false` until you release) — confirm.

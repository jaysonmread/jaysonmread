# CC Blues — the Entry Schema (v0.2 draft)

_One entry per artist, producing two aligned renders: the **car** (Experience) and the
**article** (Archive). Written to match the real `carData` contract in `car_template_v2.html`
and to obey the `FRAMING_STANDARD` and evidence canon. Supersedes v0.1. 2026-07-08._

> **What changed from v0.1 (Mr. Read's corrections, all folded in):**
> 1. **No AI, ever, in public.** Deep-research reports and the Wikipedia harvest are
>    *internal leads only* — the tools that point us at the real scholar. They can never
>    appear as a citation. Enforced structurally below (§4).
> 2. **"Spine" is dead** — and it's banned canon (`FRAMING_STANDARD`: no `substrate /
>    foundation-for`). Importance is the **API score** (§5), not a metaphor.
> 3. **The timeline is a first-class, importance-ranked, sourced structure** (§6), not a
>    two-line afterthought. 20–40 stops for a life like Lead Belly's.
> 4. **The car is formalized** to your five real stations, and **Circle** carries the full
>    circle with the economics surfaced (§3, §7).

---

## 0. The shape

One file per artist. Its frontmatter is a structured record that renders **two ways**:

```
                         one entry (lead-belly.md/.json)
                          ┌──────────────────────────┐
   THE CAR  (Experience)  │  identity + api_score     │  THE ARTICLE (Archive)
   car_template_v2.html   │  stations:                │  Pete-voice encyclopedia page
   Objects·Records·       │    objects  ─ vitrine     │  prose + {cite:} + References
   Sources·Circle·        │    records  ─ sides       │
   Timeline               │    reading  ─ volumes     │  wiki_url links car ⇄ article
   (renderCar carData)    │    circle   ─ people+scenes│
                          │    timeline ─ stops       │  api_score → Degree-of-Interest
                          │  sources[] (real only)    │     culling on the yard map
                          └──────────────────────────┘
```

The **Experience** is the selection + spatial + visual layer (the car exterior, the parlor,
day/night, the yard placement, which artifacts/sides we choose to show). The **data for all
of it lives in the entry** — the Experience authors nothing; it stages what the entry holds.

---

## 1. The `carData` contract (from `car_template_v2.html` — do not drift from this)

Your renderer already expects exactly this. The schema's job is to fill it truthfully.

```jsonc
{
  "artist": "Lead Belly",
  "canonical_db_name": "Lead Belly",         // the Master-DB (River) key
  "car_template": "work-commentary",          // = primary_node (the yard spine node)
  "group": "work-commentary",
  "wiki_url": "/archive/artists/lead-belly",  // car ⇄ Archive article link
  "identity": {
    "birth_year": 1888, "death_year": 1949,
    "birth_city": "Mooringsport", "state": "Louisiana",
    "instrument": "twelve-string guitar", "era": "songster / early folk revival"
  },
  "api_score": 0,        // 0–100, from codex-score (§5); drives map culling
  "stations": {
    "objects":  [ /* vitrine: artifacts, §7 */ ],
    "records":  [ /* sides: {recording_date, reissue_year, ...}, §7 */ ],
    "reading":  [ /* cited scholarly volumes, §7 */ ],
    "circle":   { "people": [ /* full circle */ ], "scenes": [ /* venues/circuits */ ] },
    "timeline": [ /* stops: {year, event_type, ...}, §6 */ ]
  },
  "_flags": {            // counts + gap markers the summaries read
    "objects": 0, "records": 0, "sources": 0,
    "circle_people": 0, "circle_scenes": 0, "circle_gap": false,
    "timeline": 0
  }
}
```

Field names (`recording_date`, `reissue_year`, `year_is_reissue`, `circle.people`,
`circle.scenes`, `_flags.circle_gap`, `timeline[].year`) are taken verbatim from the
template's summary builders. **New fields are additive only.**

---

## 2. Frontmatter — the full entry record (superset of `carData`)

```yaml
---
id: lead-belly
type: artist                       # artist | show | record | circle | scene | reading | timeline
canonical_db_name: "Lead Belly"
display_name: "Huddie William Ledbetter"
aliases: ["Leadbelly", "Huddie Ledbetter"]

# —— the yard's navigation (FRAMING_STANDARD spine = 4 functional-aesthetic nodes) ——
primary_node: work-commentary      # sacred-testimonial | dance-groove | work-commentary | theatrical-cosmopolitan
facets:
  region:  [{ name: "Ark-La-Tex / Texas", codified_by: "note the collector who drew the grid" }]
  era:     ["songster", "1930s–40s folk revival"]
  scenes:  [scene:shreveport-fannin-street, scene:nyc-folk-revival]   # makers' OWN venues/circuits
  lineage: [artist:blind-lemon-jefferson]                              # kinship/influence as makers traced it
world: River                        # Master-DB partition (River=roster). NAV is primary_node+facets, not world.

# —— importance (codex-score API; §5) — this is how we state importance, NOT prose metaphor ——
api_score: 0                        # 0–100 (min-max normalized)
api_tier: landmark                  # landmark | major | notable | documented   (derived from api_score bands)
degree: 0                           # distinct co-mentioned artists
corroboration: 0                    # max independent sources on a single event
catalog_size: 0
n_events: 0

identity: { birth_year: 1888, death_year: 1949, birth_city: "Mooringsport", state: "Louisiana",
            instrument: "twelve-string guitar", era: "songster / early folk revival" }

# —— lifecycle & promotion gate (auto-draft, you release) ——
status: verified                    # seed → draft → verified → published
visibility: public
published: false                    # YOU flip in batches
updated: 2026-07-08

wiki_url: /archive/artists/lead-belly

# —— PUBLIC citation ledger — REAL SOURCES ONLY (§4) ——
sources:
  - { key: wolfe-lornell-1992, kind: scholarly, author: "Charles Wolfe & Kip Lornell",
      work: "The Life and Legend of Leadbelly", year: 1992, publisher: "HarperCollins" }
  - { key: lomax-1936, kind: primary, author: "John A. Lomax & Alan Lomax",
      work: "Negro Folk Songs as Sung by Lead Belly", year: 1936 }
  - { key: santelli-2015, kind: scholarly, author: "Robert Santelli",
      work: "Lead Belly: A Man of Contradiction and Complexity", year: 2015, publisher: "Smithsonian Folkways" }
  - { key: komara-eob, kind: reference, author: "Edward Komara (ed.)",
      work: "Encyclopedia of the Blues", year: 2006 }

# —— INTERNAL leads — NEVER rendered, NEVER cited; used only to locate real sources above ——
_leads:                             # deep-research, harvests, AI syntheses live here and DIE here
  - { kind: deep_research, path: "04 — Research Reports/…", note: "points to Wolfe&Lornell p.[locate]" }
  - { kind: wikipedia_harvest, path: "Vault/05-Artists/lead-belly/Lead_Belly.md", note: "CC-BY-SA, internal only" }
---
```

---

## 3. The five car stations (canonical order, from your template)

| Station | Holds | Canon note |
|---|---|---|
| **Objects** (vitrine) | artifacts, photographs, instruments, documents ("museum pieces") | each needs provenance + a real source; `::needs-artifact` until filled |
| **Records** (cabinet) | the *sides* — recordings/releases we choose to show | `recording_date` / `reissue_year`; name session, label, personnel |
| **Sources** (reading shelf) | the cited **scholarly volumes** — the "reading content" | real books/articles only; this station *is* the visible bibliography |
| **Circle** | `{ people[], scenes[] }` — the **full** circle | producers, label founders, folklorists, family, community — **surface who profited / was erased** (name the money) |
| **Timeline** | the importance-ranked **stops** | §6 — the heart of this revision |

Stations map one-to-one to what you described. "Museum pieces" = Objects. "Albums we choose" =
Records. "Reading content" = Sources. "Circles (Lomax circle / Texas circle)" = Circle +
`scenes`. All of it is entry data; the car just stages it.

---

## 4. Citation integrity — the hard rule (structural, not advisory)

> **A claim is publishable only if it resolves to a `sources[]` entry whose `kind` is one of:
> `scholarly | primary | periodical | liner | archive | discography | reference`.**
> `deep_research`, `wikipedia_harvest`, and anything AI-generated are `_leads` — a private
> field that the renderer never reads and the linter forbids in `sources[]`. The word "AI"
> never appears in public output.

- Deep research's *only* job: point us at the real footnote. We then read that source and
  cite **it**. The DR itself is discarded from the record.
- The Wikipedia harvest (`Lead_Belly.md`) is CC-BY-SA raw material, "internal/local research
  copy only" — a lead, never a citation. ("Better than Wikipedia" = we cite the scholarship
  Wikipedia only summarizes.)
- Any unfilled claim carries `[DR-GAP]` (your existing marker). **`[DR-GAP]` blocks
  `published: true`.** A gap is honest; a fabricated or AI-sourced citation is disqualifying.
- Every citation should carry, where possible, `author, work, year, page, quote` and a
  `corroboration` count (how many independent real sources agree — the same signal the API
  score rewards).

---

## 5. Importance = the API score (replaces every "spine/foundation" instinct)

You already defined this (`codex-score_importance_DOI.md`): a deterministic
**A-Priori-Importance** score per artist and per event, from `catalog_size`, co-mention
`degree`, and source `corroboration`. It powers Degree-of-Interest culling — zoomed out, the
yard shows only high-API **landmarks**; zooming in reveals the rest.

- In prose, importance is stated in **Framing-Standard vocabulary** — *landmark, master
  practitioner, innovator, architect, radical intellectual* — and always **shown, then named**
  (demonstrate the musical action before asserting the stature). Never "spine," "root,"
  "foundation of," "godfather of," or any ladder metaphor.
- `api_tier` (derived bands of `api_score`) decides map prominence and default zoom level.
- Event selection for the timeline uses `event_api` (corroboration + `artist_api`/20) so
  landmark sessions surface first.

---

## 6. The timeline model (the real fix)

A **stop** is a typed, dated, sourced, importance-scored event. The Experience plots stops
along the car's timeline rail; the Archive lists them. Selection is by `event_api`, so a
prolific life yields 20–40 meaningful stops, a sparse one yields what it honestly has.

```yaml
timeline:
  - year: 1933
    date: "1933-07"                  # precision as available (year | year-month | full)
    event_type: documentation         # birth | emergence | composition | recording | release |
                                       # collaboration | performance | publication | carceral |
                                       # legal | award | legacy | death | encounter
    title: "John & Alan Lomax record Ledbetter at Angola for the Library of Congress"
    note: >
      Framing-locked: recorded/documented, NOT 'discovered'. The Library of Congress
      sessions are access and documentation; the artist and his repertoire already existed.
    place: "Louisiana State Penitentiary (Angola)"
    related: [artist:john-lomax, artist:alan-lomax, scene:angola-prison-songs]
    event_api: 0
    corroboration: 0
    sources: [wolfe-lornell-1992, lomax-1936]     # real keys from sources[]
    source_page: "[locate]"                         # honest placeholder, never invented
```

**Worked Lead Belly spine of stops** (illustrative selection; each needs its real
`source_page`/`quote` filled from `sources[]`, none from a lead):

| Year | Type | Stop (framing-locked) |
|---|---|---|
| 1888 | birth | Born near Mooringsport, Louisiana (birth-year contested across census/records — *show the dispute*) |
| c.1903 | emergence | A working "musicianer" in Shreveport's Fannin Street district |
| c.1912 | composition | Writes "The Titanic," his first twelve-string composition; performing around Dallas with Blind Lemon Jefferson |
| 1918 | carceral | Imprisoned (as Walter Boyd), Imperial Farm, Sugar Land, Texas |
| 1925 | carceral | Pardoned by Gov. Pat Neff after a petition song |
| 1930 | carceral | Sentenced to Angola |
| 1933 | documentation | The Lomaxes **record** him at Angola for the Library of Congress |
| 1934 | biographical | Released; travels with John Lomax collecting songs |
| 1935 | recording | ARC sessions, NYC (53 takes, six released across six labels) |
| 1936 | publication | *Negro Folk Songs as Sung by Lead Belly* (Lomax) published |
| 1939 | protest/carceral | Rikers term; records "Bourgeois Blues" and "Scottsboro Boys" (early "stay woke") — **conscious critique, not victimhood** |
| 1940 | recording | RCA Victor's *The Midnight Special and Other Southern Prison Songs*, with the Golden Gate Quartet |
| 1941–47 | recording/circle | Folkways/Asch sessions; NYC folk scene with Woody Guthrie, Pete Seeger, Sonny Terry, Brownie McGhee |
| 1944 | recording | Capitol sessions, California |
| Jun 1949 | performance | Final concert, UT Austin — a tribute to John Lomax |
| Dec 1949 | death | Dies in New York City (ALS) |
| 1950 | legacy | The Weavers' "Goodnight Irene" reaches #1 (~2M copies) — the first folk song to top the U.S. charts |
| 1988 | award | Inducted, Rock and Roll Hall of Fame |

That's 18 landmark stops before granularity; the full curated set clears 30. The **economics
stop** — Ledbetter *sued* John Lomax over withheld earnings and won release from the
management contract — is a Circle/timeline crossover that the Framing Standard *requires* us
to name.

---

## 7. Records, Objects, Circle — field detail

```yaml
stations:
  objects:                          # vitrine / museum pieces
    - { title: "Stella twelve-string guitar", kind: instrument,
        image: "::needs-artifact", provenance: "…", sources: [wolfe-lornell-1992] }
  records:                          # sides we choose to show
    - { title: "The Midnight Special and Other Southern Prison Songs", label: "RCA Victor",
        recording_date: "1940-06-15", personnel: ["Golden Gate Quartet"], sources: [santelli-2015] }
  reading:                          # the visible bibliography (real volumes only)
    - { work_title: "The Life and Legend of Leadbelly", author: "Wolfe & Lornell", year: 1992,
        source_key: wolfe-lornell-1992, relevance: "standard biography" }
  circle:
    people:                         # FULL circle — surface roles AND economics
      - { name: "John A. Lomax", role: "folklorist / manager",
          note: "documentation & business; contract dispute — Ledbetter sued for withheld earnings", ref: artist:john-lomax }
      - { name: "Alan Lomax", role: "folklorist", ref: artist:alan-lomax }
      - { name: "Martha Promise", role: "wife; billed as manager", ref: person:martha-promise }
      - { name: "Moses Asch", role: "label founder (Folkways)", ref: person:moe-asch }
      - { name: "Blind Lemon Jefferson", role: "collaborator (Dallas)", ref: artist:blind-lemon-jefferson }
    scenes:                         # the artist's OWN venues/circuits, not collector zones
      - { ref: scene:shreveport-fannin-street, name: "Fannin Street / St. Paul's Bottoms, Shreveport" }
      - { ref: scene:nyc-folk-revival, name: "New York folk revival" }
```

**Circles/scenes are their own entries (cars) the artist couples to** — `circle:lomax-circle`,
`scene:nyc-folk-revival`, `scene:shreveport-fannin-street`. That's your "belongs to the Lomax
car *and* the Texas car": the artist's `facets.scenes` / `circle` list the couplings; each
referenced circle/scene is its own entry that renders its own car with member portraits.

---

## 8. Open for your call
1. **`primary_node` for Lead Belly** — I set `work-commentary` (prison/work songs, conscious
   critique) with facets reaching Sacred and Theatrical. Agree, or does he sit elsewhere?
2. **`api_tier` bands** — what score cutoffs map to landmark / major / notable / documented?
3. **`{cite:key}` inline marker** — keep, or match an existing convention in the cars?
4. **River/Rail/Record/Road** — confirm what each Master-DB partition means so `world` is right.
5. Should I now **build the real Lead Belly entry** (fill every `[locate]` from the actual
   scholarship, real `api_score`) as the v0.2 stress test?

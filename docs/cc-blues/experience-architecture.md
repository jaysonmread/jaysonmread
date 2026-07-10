# CC Blues — the Experience Architecture (Six Worlds)

_Integrates the ChatGPT 5.6 review ("Six Ways the Blues Moves" + the image-campaign
critique) with our entry schema and the Framing/evidence canon. 2026-07-08._

---

## 0. The one insight that reorganizes everything

> **The Archive is the Experience's READ MODE.** They are not two builds. Every world page
> carries a `READ MODE` control that flattens the spatial scene into an accessible linear
> article of the same callouts + citations. The "better-than-Wikipedia" Archive *is* that
> linear view; the "video-game" Experience is the spatial view. **One entry, one build, two
> views.** This collapses the old Archive-track and Experience-track into a single pipeline
> over the entry schema.

```
                         the entry (per subject)
                                  │
                render into a world page (spatial)  ──►  THE EXPERIENCE  (drag/zoom/listen)
                                  │  READ MODE
                                  └──────────────────►  THE ARCHIVE  (linear article + Paper Trail)
```

---

## 1. Six worlds = six verbs

The blues is not one line of development; it is music **moving** through time, place, bodies,
machines, institutions, memory, and argument. Six navigable worlds, each answering a
different historical question. One subject can appear in all six.

| World | Verb | Core question |
|---|---|---|
| **RAIL** | assembles | How is this history assembled into a journey? (the archive's own structure: show trains, cars, yard, roundhouse) |
| **RIVER** | carries | How do songs, practices, memories, influences flow through time? (continuity without a single origin) |
| **ROAD** | moves | Where did people, songs, instruments, labor, markets travel? (migration, touring, the automobile, the *broken* road) |
| **RECORD** | **spins** | What survives as sound made into things? Labels, discs, vinyl, sheet music & piano rolls, field discs, unissued takes — the chain performance → take → object → reissue. (Verb locked 2026-07-10; "fixes" and "keeps" rejected.) |
| **READING** | **tells** | Who has told this history — as ledger (facts), witness (firsthand), or argument (interpretation)? ("Interprets" rejected as over-claiming; "tells" covers all three registers.) |
| **RADIO** | transmits | What could people hear, where, placed by whom, with what effect? (broadcast as listening history) |

- **The Concourse** is the homepage/transfer point — the Florence, AL depot at night, six
  departures, and a **suspended station clock** that sets the historical period for the whole
  archive at once (time is a global property, not a separate timeline page).
- **The pinned journey ticket** is the connective spine: pin Muddy Waters (or a song, place,
  concept) and each world reveals *his* layer. "The same recording has not changed. The
  question being asked of it has changed." That is the central intellectual experience.

---

## 2. One interaction grammar (learn once, works in every world)

1. **Four zoom levels — Horizon → District → Artifact → Receipt.** Wonder → explanation →
   evidence. **Horizon culling = our API score** (`Degree of Interest`: only landmarks render
   zoomed out). **Receipt view** exposes: source · page/claim-ID · quotation/paraphrase ·
   evidence class · uncertainty · contradiction · related recordings — i.e. our `sources[]`
   entry, verbatim.
2. **Five callout types** — every label is exactly one, each with its own marker shape; color
   encodes function, not decoration:
   - **PLACE** (city, venue, river, station, studio) · **PERSON** (artist, broadcaster,
     producer, scholar, collector) · **SOUND** (song, recording, riff, verse, instrument,
     practice) · **SYSTEM** (label, railroad, network, migration corridor, institution) ·
     **QUESTION** (disagreement, myth, missing evidence, unresolved date).
3. **Two layers of writing** — a callout opens with **What happened** (plain fact) + **Why it
   matters** (1–2 sentences); an expandable **Paper Trail** holds citations, qualifications,
   alternate claims. This is the anti-"illustration-covered-in-essays" rule.
4. **Persistent listening** — a record-player/radio dock follows the visitor across worlds
   (track, artist, date, place, show, world). The audio is the thread, not decoration.
5. **Carry a thread** — the pinned journey ticket (see §1).

**Per-page control rail (identical everywhere):** `MAP · TIME · LISTEN · THREAD · LAYERS ·
READ MODE · RETURN`. `LAYERS` toggles people/recordings/places/systems/arguments/questions.
`RETURN` goes to the Concourse without dropping the pinned thread.

---

## 3. How this reconciles with the entry schema (v0.2 → v0.3 deltas)

The car schema still holds — it is the **Rail face** of an artist. The entry gains a thin
layer so the *same* record renders into any world:

- **`world` becomes `worlds: []`** — a subject can live in several (rail, river, road,
  record, reading, radio). Each world reads the facet it needs (timeline→River,
  migration→Road, sessions→Record, interpretation+sources→Reading, broadcasts→Radio, the
  car→Rail).
- **`callout_type`** on every entry/relation — `place | person | sound | system | question` —
  drives marker shape on the map. (Maps onto our `type`: artist/circle-member = person,
  scene/venue = place, record/track = sound, label/circle/network = system.)
- **`QUESTION` is now a first-class entry type.** The "Repair Track" (missing transcript,
  disputed date, provisional subtheme, broken link, insufficient source) and the "Argument
  Wall" are *published* uncertainty. This is where `[DR-GAP]`, `contradictions.md`, and
  `open-questions.md` surface as citizens — uncertainty as part of the working yard, "rather
  than an embarrassing footnote."
- **Receipt view = the `sources[]` entry; Paper Trail = the References render.** No new data
  model — the callout's two-layer writing is `summary`/`why_it_matters` + `sources[]`.
- **Evidence class** = our `sources[].kind`; **uncertainty/contradiction** = `confidence` +
  links to QUESTION entries. Still: **only real sources publish; `_leads`/AI never do.**

---

## 4. The visual-production discipline (Part A of the review, adopted)

The image campaigns are a strong *visual sketchbook*, not yet a finished asset system. The
next phase is **editing, not inventing.**

**Three locked visual registers** (stop the two-house-style drift):
- **A — The living world:** saturated chromolithograph color. Hero pages, River, Road,
  Concourse, major maps.
- **B — The railroad archive at night:** black, sepia, indigo, cream, amber. Show trains, car
  diagrams, ledgers, the working yard.
- **C — Documentary evidence:** cream, black ink, restrained rules. Transcripts, citations,
  labels, track metadata, source pages.
- Per-world tints stay within this DNA (Rail nocturnal/brass; River blue/flood-brown; Road
  dust-red/sign-yellow; Record shellac/label-red; Reading warm-paper/editorial-red; Radio
  midnight-blue/phosphor-green).

**The image-text law (matches our no-AI-facts rule, extended to pixels):**
1. Generate the car, plaques, borders, **blank** signboards. 2. Preserve large text-safe
   spaces. 3. Overlay every title, fact, number, date, citation **deterministically**. 4.
   Pull that text from the canonical DB. 5. Keep generated lettering only where it carries no
   factual meaning. **Generated faces are never used; real archival photographs sit in the
   empty portrait windows.**

**Category body-language** (so cars differ by silhouette, not just labels — labels being the
least reliable part of a generated image): Artist car = distinctive personal object; Circle
car = round-table geometry + named seats; Record car = shelves/horns/disc circles; Show car =
route board + show number; Caboose = retrospective ledger; District car = map/herald; Motive
power = mechanical, near-zero text.

**Component hierarchy** (posters don't reduce to phones): whole-train hero → single-car card
→ car-window detail → emblem → title plaque → portrait frame → mobile thumbnail. Re-render
each; stop cropping six-pane sheets. Export sizes per winner: 16:9 hero, 3:1 banner, 4:5
card, 1:1 tile, 9:16 mobile, isolated object, blank-text, typography-overlaid.

**The earn-its-place test for any rail image:** *what does this teach that an ordinary train
illustration could not?* (repertoire transmission, show sequence, personnel, migration,
recording history, influence, regional movement, source evidence, historical disagreement).

---

## 5. Build sequence (reconciled: GPT phases + our entry-first proof)

1. **Prove one entry end-to-end (Lead Belly):** entry → Rail car (carData) → READ-MODE Archive
   article, every fact from real sources. Smallest complete loop; validates schema v0.3.
2. **Freeze broad image generation; select ~30 canonical winners** (5 train/show, 5
   architecture, 5 River/Road/Record explanatory, 5 car interiors, 5 artist/Circle forms, 5
   interface objects); lock the three registers; complete the archival-photo pipeline.
3. **Build one gold-standard show (Show 001)** as the first full Rail vertical slice:
   Concourse departure → full consist → movement stops → artist cars → Circle car →
   Record/evidence car → caboose recap → River/Road links → return to Concourse.
4. **Shared mega-page engine** (pan/zoom, callout anchoring, minimap, evidence drawer,
   persistent audio, pinned thread, READ MODE) — build once, reuse across worlds.
5. **Then Record + Reading** (credibility), **River + Road** (time + geography), **Radio**
   (combines all), **cross-world journeys** (Muddy Waters; the Great Migration; women and the
   commercial blues; the making of the Delta canon; the blues on the radio).

---

## 6. Open decisions carried forward
1. First proof: **one artist (Lead Belly)** vs **one show (Show 001)** first? (Recommend
   artist first — smaller loop — then Show 001.)
2. `worlds: []` membership rules — does every artist get all six faces, or only where there's
   real material (gaps become QUESTION entries)?
3. Where does the "ruling workbook" for the 30 winners live, and who scores them?

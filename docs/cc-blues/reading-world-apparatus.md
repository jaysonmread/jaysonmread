# CC Blues — the Reading World Apparatus (v0.1)

_The critical machinery for READING tells: camps, positionality, purpose, and the source
dossier. Internal foundation document — public rendering happens through the Reading world's
Source Stacks, Guiding Lights table, Argument Wall, and Language Desk. Drafted 2026-07-10._

---

## 0. Charter

READING is the world of everything *told* about the blues — ledger, witness, and argument.
Its job is not to rank books but to **position** them: every source enters the archive with
its camp coordinates, its author's positionality, its declared and operative purpose, and a
ruling on what it can and cannot be trusted for. Wikipedia treats sources as interchangeable
citations; CC Blues treats them as positioned documents. That difference is the product.

Two laws govern the whole apparatus:

1. **The classification-yard rule applies to scholarship.** Camps are our construction —
   useful, visible, and revisable. Works get coordinates, not boxes; the switch stand works
   on books too. The camp taxonomy itself hangs on the Argument Wall as an argument.
2. **The double-reading rule.** Every source is evidence twice: as an **argument about its
   subject** and as a **witness of its own moment**. It can fail as the first and be
   priceless as the second. The archive never burns a book; it re-shelves it.

---

## 1. The camps (working taxonomy — provisional, ratify by clustering)

| # | Camp | Era | Exemplars | Operative purpose | Position in one line |
|---|------|-----|-----------|-------------------|----------------------|
| 1 | Founding Black intelligentsia | 1920s–40s | Sterling Brown, Alain Locke, Zora Neale Hurston, John Work III | claim the music as serious Black culture | insiders/adjacent scholars, later under-cited; Work's Coahoma fieldwork buried under Lomax's name until *Lost Delta Found* (2005) |
| 2 | Folklorist-collectors | 1930s–60s | John & Alan Lomax, Library of Congress orbit | preserve + make national heritage | white institutional gatekeepers; John Lomax was Lead Belly's *manager* while authoring him |
| 3 | Romantic rediscovery | 1959–70s | Charters (*The Country Blues*), McKune circle / "Blues Mafia," rediscovery expeditions | canonize + romance | white urban collectors; knew the music as rare objects first; their holdings appreciated with the canon they wrote |
| 4 | British documentary | 1950s–70s | Paul Oliver, Tony Russell, Bruce Bastin, *Blues Unlimited* | document exhaustively | transatlantic distance — records and correspondence before ever visiting; rigor and exoticism risk |
| 5 | Discographer-ledger | ongoing | Godrich & Dixon (& Rye), Wardlow, *78 Quarterly* | fix the factual record | object-centered; quietly the most durable camp; nearly pure ledger |
| 6 | Black nationalist reclamation | 1963– | Baraka (*Blues People*), Larry Neal | reclaim politically | blues as the historical consciousness of Black America |
| 7 | Affirmation school | 1964– | Ellison (contra Baraka), Albert Murray (*Stomping the Blues*) | rescue the art from sociology | blues as heroic craft and Black modernity, against both pathology and primitivist romance |
| 8 | Academic ethnomusicology / folkloristics | 1970s– | Titon, David Evans, Ferris; *Living Blues* (1970, Black-artists-only editorial line) | theorize via fieldwork | institutionalization of blues studies; a magazine's coverage policy as a camp position |
| 9 | Black feminist recovery | 1980s– | Daphne Duval Harrison, Hazel Carby, Angela Davis | correct the male canon | restores the blues queens the collector canon was built against |
| 10 | Vernacular theory | 1980s– | Houston Baker, Clyde Woods ("blues epistemology") | blues as a way of knowing | literary/geographic theory |
| 11 | Revisionist historiography | 2000s– | Wald, Hamilton, Filene, Miller, Gussow, Abbott & Seroff (Black press method), M. Morrison (*Blacksound*) | correct the canon's making | the lens turned on the collectors and the industry itself |
| 12 | Witness literature | 1941– | Handy (*Father of the Blues*), Broonzy, Willie Dixon, Honeyboy Edwards | testify / manage legacy | artists' own accounts, with mediation *inside* the witness (co-writers, audiences performed to) |

Notes:
- A work can hold membership in several camps (Gussow is 8 + 11 + a practicing harmonica
  player — practitioner positionality he analyzes himself).
- **The archive's own shelf is positioned**: the Framing Standard's grounds (Morrison, Hunt,
  Gussow, Miller, Filene, Hamilton + Maultsby/Wilson/Ramsey) place CC Blues in the lineage of
  camps 1 and 11. The Reading world states this publicly (see §6) instead of floating above it.
- Public-facing label may be "schools" or "traditions"; internal working name stays "camps"
  because it is honest about partisanship.

## 2. Positionality axes (recorded per author–work pair)

Positionality can shift between an author's works — Alan Lomax 1936 ≠ Alan Lomax 1993 — so
the profile attaches to the pair, not the person.

1. **Relation to the culture** — insider / community-adjacent / outsider. Named plainly.
2. **Relation to the money** — the axis most often hidden and the one the Framing Standard
   requires: collector (holdings appreciate with the canon), rights-holder, manager,
   label/reissue operator (liner notes = sales documents wearing scholarship's clothes),
   promoter, working musician, none-known.
3. **Relation to the evidence** — fieldworker / interviewer / records-and-paper /
   synthesizer. Distance in miles and years.
4. **Market served** — academic press, trade, fanzine, mass market, promotional.
5. **Method transparency** — shows receipts (named informants, cited sessions) vs. narrated
   authority.
6. **Gender and the canon** — who the work permits to be "deep."
7. **Institutional power** — funding, publishing access, the power to bury (Work III).
8. **Nationality / distance** — the British mediation; the romance of the outsider.

## 3. Purpose taxonomy (declared vs. operative)

Vocabulary: **document · preserve · canonize · sell · romance · reclaim · theorize ·
testify · correct · entertain.**

- `declared`: what the preface/introduction claims.
- `operative`: what the book actually does (usually primary + 1–2 secondaries).
- Evidence for the gap between them: publisher and market, funding, what the work chooses to
  omit, how it handles counter-evidence, what it was used for after publication.

## 4. The source dossier (the working template — fill while reading)

```yaml
# one file per work, in the foundation (Wiki sources/ namespace)
source_id: charters-1959-country-blues
biblio: { author: "Samuel Charters", title: "The Country Blues", year: 1959, publisher: "Rinehart" }
reading_register_mix: { ledger: low, witness: mid, argument: high }   # can vary by chapter

camps: [ { camp: romantic-rediscovery, weight: primary } ]            # provisional on intake
positionality:
  relation_to_culture: outsider
  relation_to_money: "collector; tied to reissue activity of the era"
  relation_to_evidence: "records + interviews; limited fieldwork"
  market: mass
  method_transparency: low
  notes: ""
purpose:
  declared: [document, preserve]
  operative: [canonize, romance]
  evidence: "author's own later admissions; publication context"

claims: []               # load-bearing claims extracted while reading, each with locator
                         #   - { claim: "", locator: "p.__", supports: [], contradicts: [] }
inherits_from: []        # chain of custody — whose research this depends on
transmits: []            # myths/errors it propagated downstream (error genealogy)

ruling:                  # the archive's usage guidance — the payoff field
  reliable_for: []       #   e.g. "what the 1959 revival believed and wanted"
  unreliable_for: []     #   e.g. "1920s biographical fact"
  witness_value: ""      # what this work is PRIMARY evidence of (its own moment)
  framing_scan: []       # discovery language, primitivism, erasures — quote-and-date if used
  status: provisional    # provisional → ratified (council pass)
```

Dossier fields feed the public Reading surfaces directly: `ruling` → the Guiding Lights
pages and source cards; `claims` + `contradicts` → the Argument Wall; `positionality` +
`purpose` → the comparison table; camp vocabulary → the Language Desk.

## 5. Evidence integrity rules this apparatus enforces

1. **Independence, not citation count.** Corroboration counts *independent lines*: five
   books inheriting one 1959 claim are one source. `inherits_from` makes dependence
   computable; the corroboration badge respects it.
2. **Error genealogies are content.** Myth transmission through the literature renders like
   floating verses through the River — same mechanics, and publicly fascinating.
3. **The double reading is mandatory.** No source gets dismissed without its
   `witness_value` being recorded. Re-shelve, never burn.
4. **Framing violations are quoted-and-dated, never repeated in the archive's own voice.**
5. **Register-aware weighing.** A ledger, a witness, and an argument corroborate
   differently; the comparison table says which registers are in play.

## 6. The archive's self-dossier

The Reading world publishes a dossier *on CC Blues itself*: the steward posture, the
Framing Standard's grounds and camps, Mr. Read's positionality (named the way we'd name
anyone's), what the archive is reliable for, and where it remains uncertain. Wikipedia's
weakness is pretending a view from nowhere; the archive's credibility move is a view from
somewhere, stated. This page is also where the harmful-language statement and the
promotion-gate policy live in public.

## 7. Logistics — the working loop (starting now)

1. **Intake**: open a dossier the day you open the book; provisional camp tag; positionality
   sketch from what's already known.
2. **While reading**: extract load-bearing claims with locators into `claims[]`; log
   inheritance whenever the author leans on someone else's research.
3. **Collision**: any disagreement between two dossiers births an Argument Wall QUESTION
   entry immediately — don't batch these; the collision is the insight.
4. **Ruling**: on finishing, write `reliable_for / unreliable_for / witness_value` — the
   usage guidance is the dossier's whole purpose.
5. **Ratification pass** (periodic council): confirm camps by clustering across dossiers,
   reconcile rulings, promote to `ratified`, log via the wiki tool loop.
6. **Feed the corpus**: dossiers join the 39k-file scholarly zone / 2,521 passages as the
   *interpretive index over* them — the dossier layer is what makes that mass navigable.

## 8. Open threads

- Public label for camps ("schools of blues thought"?) — Language Desk decision.
- Whether `camps` renders publicly per-source or only through the Guiding Lights synthesis.
- Ratification cadence and who sits the council (you + which agent lanes).
- First dossier: whatever is open on Mr. Read's desk right now.

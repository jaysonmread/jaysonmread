# CC Blues — Google Drive Map & Scholarly Corpus

_The project lives in Google Drive, not this repo. These IDs and structures were discovered
across this conversation and are expensive to re-derive — treat this as the map. IDs are
stable; folder *contents* and the MCP server ID are not. 2026-07-15._

> **How to read Drive (see `04-environment-and-tooling.md` for full detail):** load the Google
> Drive MCP via ToolSearch. `search_files` uses a structured query language; the file-title
> field is **`title`** (not `name`). Results are often huge and get spilled to a file — parse
> with `jq`. `read_file_content` works on `.md`/`.csv` even though not "officially" listed.

---

## 1. Top-level topology

```
My Drive/
└── CC Blues Archive V2/                         [root]  id: 1X7VEStoW25RY9rf2gCA5wFffll_8qIEo
    ├── CC Blues Wiki/                            [THE FOUNDATION — LLM synthesis wiki, "FINAL_ROOT", ~1,234 files]
    │                                             id: 1UxLLS6fJUQ6wwg48cGiLRAkcNX2A_T83
    │     ├── artists/ (163)  broadcasts/ (78)  concepts/ (120)  minds/  law/
    │     ├── _data/ (400)  _tools/ (8: wiki_index.py, wiki_log.py, wiki_lint.py, wiki_common.py)
    │     ├── index.md  contradictions.md  open-questions.md  log.md  search_index.json
    │     └── atlas/  scripts/  campaigns/   [GD-19 self-map, merged here from staging]
    │           atlas    id: 1diFTcgWYSKo49dq4Lj6ZE5KmNlozR33N
    │           scripts  id: 1flgNH6ke68-G9thDQ3Bbr4MWTPT2jqnR   (registry.md, graveyard.md, wiki-* pages)
    │           campaigns id: 1c1ckSU1DnxEEOyVt8FXLCA3Ee0sxGMFw
    │     └── sources/dr/   [deep-research namespace — INTERNAL leads]
    ├── CC Blues Archive/                          [numbered zones — mixed private/publish-source]
    │     ├── 01 — Master Database/     River / Rail / Record / Road workbooks (Mr. Read writes; DO NOT touch xlsx programmatically)
    │     ├── 02 — Show Research/       per-show dispatches, subtheme CSVs, "Pete enrichments"
    │     ├── 03 — Scholarly Sources/   [~39,448 files] THE CORPUS — see §3
    │     ├── 04 — Research Reports/    Gemini/GPT/Perplexity deep research  [INTERNAL leads only]
    │     ├── 05 — Site Design/         visual briefings, style-lock campaigns, comparative studies
    │     ├── 06 — Notebook Transcriptions/
    │     ├── 07 — Handoffs and Session Logs/   (STATE_OF_THE_ARCHIVE maps live here)
    │     ├── 08 — Scripts and Tools/   build_lean_site.py, dashboard scripts, census scripts
    │     ├── 09 — CC Hub/       ├── 10 — Timeline Campaign/ (codex-score outputs)   └── 99 — Old Versions/
    ├── CC Blues Vault/                            [Obsidian typed-entity wiki, ~75,374 files]
    │     ├── 00-Inbox/ (~53k — rent-party staging)  01-Standing-Rules/  02-Session-Logs/  03-Decisions/
    │     ├── 04-Agent-Roster/  05-Artists/ (1,174)  06-Shows/ (4,379)  07-Stories/  08-Influences/ (296)
    │     ├── 09-References/  10-FloatingVerses/  12-Passages/  13-Dossiers/
    │     ├── _canon/  (00_INDEX.md, FRAMING_STANDARD, TRAIN_DEPOT_ARCHITECTURE, LOMAX_EQUALS_GEMINI_CANON)
    │     └── CLAUDE.md  (standing orders)
    ├── CC Blues Sources/                          [raw fuel, ~8,904 files, gitignored, Drive-sync protected]
    │     └── passages/ (2,521)  passage_dossiers/ (322)  notebook/ (431)  narrations/ (154)  pdfs/ (112)  extracted_text/ (391)  lyrics/  counter_critics/
    └── cc-blues-poc/                              [the live POC = ccblues.com; lean static site → Netlify]
          └── site/ (1,557)  covers/ (100)  data/ (14)  shows/1/index.html  dashboard.html  netlify.toml
```

**Note on the atlas mirror:** the GD-19 `atlas/scripts/campaigns` exist in two places — a
staging "return" (`.../GD-19/...`, id `1FlSzDPwPUD56lqX9MEOCNIFcm6QyRXNl`) and the merged
canonical copy under `CC Blues Wiki/` above. The merge step is called "Hammer."

## 2. Key file IDs (the ones you'll actually reach for)

| File | What it is | ID |
|---|---|---|
| `car_template_v2.html` | **the real `carData` UI contract** — read the `<script>`: `renderCar()` + summary builders define the data model | `1K51kqk_CS-Ag5zZsv-KBuC3iTx3O60sG` |
| `2026-06-17_FRAMING_STANDARD_...md` | the language/organization canon (LOCKED) | `19TG1Unpa1JEZLHaC9nSRr6ajZN-OmRMo` |
| `codex-score_importance_DOI.md` | the API-importance scoring method | `1vrqHs5cafJK7gacXl-HBUmdnu5FB2wO2` |
| `artist_importance.csv` | per-artist API scores (179 KB) | `1sqdJ9VIrQo53CNxohqt6G5fzYkkW_RQN` |
| `event_importance.csv` | per-event API scores (751 KB) | `1mQIgZ5k_7H4oDrLP_KZQIiLxEwl5tCM6` |
| `sources.csv` | **the corpus registry of record** (162,563 claims) | `19X_El-a8B79-4U7p2AqGq5Ya68b3teUr` |
| `koonaklaster.md` | Fahey's law (R11–R13) as a wiki concept page | `1tf3u1NklNycK-S9lglPNMpZ99IqKmd_0` |
| `fahey_patton_thesis.md` | example source dossier page (Tier 1) | `1J3OloT2H9YWzQKMU05Kv3RvG7y4RjOIJ` |
| `Lead_Belly.md` | **Wikipedia harvest** (44 KB) — INTERNAL lead, not citable | `1YPNvQVAgqLeGe40VzZtS-c3JGJA-R485` |
| `lead-belly.json` | ~1 MB structured Lead Belly data (Experience fuel) | `1blHkLWsjCDSKIW2K-8GJd5PBWF-2zShf` |
| Zone 03 `pdfs/` folder | raw scholarly PDFs + `imported_drive_dump/` | `1xyimqta8sqPGfL3ETXaGYXOWWw-8dEie` |
| car-HTML fleet folder | ~30 pre-built artist car pages (`car_lead-belly.html`, etc.) | `1I2hXJjrUwBSA2KPDDi9trS1nV43PKoSq` |

The `sources.csv` `metadata_yaml_path` column points at each work's `_parsed/<slug>/
metadata.yaml` (Windows paths — the machine of record is `C:/Users/jayso/My Drive/...`).

## 3. The scholarly corpus — what's actually on the shelf

Registry: `sources.csv` (Zone 03 `_parsed/`). **Always assign camps / hunt holes against this
file, not memory.** Selected holdings with claim counts (the number the archive has parsed):

**Reference / ledger:** Komara *Encyclopedia of the Blues* (Tier 1, **43,365**), Rolling Stone
Jazz&Blues guide (20,855), New Encyclopedia of Southern Culture: Music (4,123). Discographies:
Dixon & Godrich *Blues & Gospel Records 1902–1942* + *Recording the Blues*; Leadbitter & Slaven
*Blues Records 1943–1966*; Taft concordance; Calt *Barrelhouse Words* (Tier 1); Ford bibliography.

**British documentary (camp 4), in depth:** Paul Oliver ×4 (*Aspects of the Blues Tradition*
3,808; *Story of the Blues* 3,607; *Savannah Syncopators*; *Blues Fell This Morning* via
related) **plus O'Connell 2015 — a biography *of* Oliver** (can already do historiography-of-
Oliver). Rowe *Chicago Breakdown*.

**Rediscovery (camp 3), watchable across two decades:** Charters ×4 (1959 *Country Blues*;
1963 *Poetry of the Blues*; 1967 *Bluesmen*; 1977 *Legacy of the Blues*). Cook 1973; Oster 1969.

**Analysis / revisionist / nationalist:** Fahey *Charley Patton* thesis (Tier 1, **763**,
OCR-rescued); Baraka/Jones 1963 *Blues People* (2,469); Titon *Down Home Blues*; Ferris; Palmer
*Deep Blues* (5,451); Gussow 2020 (5,299); Wald 2010 (1,167) [only the Very Short Intro, not
*Escaping the Delta*]; Filene *Romancing the Folk* (registered); Julia Simon 2023; Huber 2013
*Black Hillbillies*; Retman 2020 *Memphis Minnie*.

**Witness seeds:** **Perry Bradford *Born with the Blues* (1,682)**; Alberta Hunter; Handy
*Blues: An Anthology* (717); Lomax 1936 *Negro Folk Songs as Sung by Lead Belly* (2,412);
*Blues in the Mississippi Night* liner.

**Woody research bed** (registered, mostly unparsed): Klein *Woody Guthrie: A Life* (Tier 1);
Reuss 1970; Briley 2006; Pascal 1990; Blake 2006 dissertation; the Smithsonian Folkways liner
corpus; Nora Guthrie oral history.

**Web-archive era:** ~28 "OIA" dossiers (Tier 3, **Gemini DR** — correctly flagged
`AWAITING_WALT_VERIFICATION` / `INGESTED_PER_DR`; these are INTERNAL leads, not citable).

## 4. The corpus HOLES (prioritized acquisition audit, 2026-07-10)

**Priority 1 — absences that strain the archive's own laws:**
1. ***Lost Delta Found*** (Work/Jones/Adams 2005) — recovered Black Fisk fieldwork buried
   under Lomax's name; the keystone positionality exhibit, not on the shelf.
2. **Calt & Wardlow, *King of the Delta Blues* (Patton)** — without it, Patton single-sources
   to the Fahey thesis (violates the independence rule the corroboration badge depends on).
3. **Alan Lomax *The Land Where the Blues Began* (1993)** — the late self-canonizing Lomax.
4. **Albert Murray *Stomping the Blues* + Ellison essays** — the **affirmation school is
   entirely absent**, yet the Framing Standard's "conscious critique, not victimhood" is
   their position. The law cites a camp the corpus doesn't hold.
5. **Hamilton *In Search of the Blues* + Miller *Segregating Sound*** — the Framing Standard's
   own cited grounds, absent as texts (parse Filene too).
6. **Wald *Escaping the Delta* (2004)** and **Greil Marcus (*The Old, Weird America*)** — half
   the Marcus–Fahey arbitration has no registered text.

**Priority 2 — the camp-13 primaries (scholarship *about* them exists; *they* are missing):**
Seeger *The Incompleat Folksinger* / Sing Out! columns; **Woody *Bound for Glory*** / collected
*Woody Sez*; Dylan *Chronicles Vol. 1* + Nobel lecture; **_Hard Hitting Songs for Hard-Hit
People_** (Lomax compiled / Woody annotated / Seeger transcribed — all three in one object);
Fahey *How Bluegrass Music Destroyed My Life* + Revenant Patton box writings.

**Priority 3 — canon depth:** Keil *Urban Blues*; Evans *Big Road Blues*; Abbott & Seroff (Black-
press bedrock); Harrison *Black Pearls* + Carby + Davis (registered, parse it); the witness
shelf (Handy *Father of the Blues*, Broonzy, Willie Dixon, Honeyboy, B.B.); 1920s academic
collectors (Odum & Johnson, Scarborough, White); Hurston *Mules and Men*; Wardlow *Chasin' That
Devil Music*; Baker / Woods / Garon; a *Living Blues* / *Blues Unlimited* run.

## 5. What "yesterday's progress" was (for context)

The session before this conversation (≈2026-07-07/08) ran a **GD-19 "atlas" pass** (a self-map
of the whole estate — one page per zone, a 198-script census in `registry.md`, campaign logs,
`contradictions-found.md`) and **Rent Party 11 — "the wiki pour"** (11 parallel agent lanes
poured seed pages into `_returns/`, Hammer-merged into `CC Blues Wiki/`). The wiki toolchain
(`wiki_index.py` → index + search_index.json; `wiki_log.py`; `wiki_lint.py`) is registered LIVE.

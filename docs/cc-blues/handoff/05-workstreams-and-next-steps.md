# CC Blues — Workstreams & Next Steps

_Where each thread stands and the concrete next action for each. 2026-07-15._

---

## Status legend
✅ done / locked · 🟡 drafted, needs work · 🔲 not started · ⏳ waiting on Mr. Read or ChatGPT

---

## A. Conceptual model & canon
**Status:** ✅ Locked. Foundation → two public renders (Archive = READ MODE of Experience);
six worlds/verbs locked; Framing Standard, no-AI law, Koonaklaster, promotion gate all settled.
**Docs:** `wiki-archive-experience.md`, `handoff/01-vision-and-model.md`, `handoff/02-locked-canon.md`.
**Next:** nothing pending unless Mr. Read reopens something. This is the stable base.

## B. The entry schema (the single load-bearing contract)
**Status:** 🟡 v0.2 committed; v0.3 deltas noted but not consolidated; **no real entry built yet.**
**What exists:** `entry-schema.md` — one file per subject; matches the real `carData` contract
(`identity`, `stations{objects,records,reading,circle{people,scenes},timeline}`, `_flags`,
`wiki_url`); citation law baked in (`sources[]` real-only vs private `_leads`); a rich
event-typed timeline model; `worlds[]`, `callout_type`, QUESTION as a first-class type; the
API-score/promotion-gate fields.
**Open (from ChatGPT reconciliation, in `04`'s uploaded spec):** add the normalized entry
model (`entry_type`, `relationships[]` with typed verbs + evidence, top-level `events[] /
record_objects[] / places[] / questions[]`, an `evidence[]` block with `source_class /
reading_register / record_role / corroboration_count / publication_block`), and a **separate
`ui_state` contract** (clicks never write canonical). These should extend the single schema,
not fork it.
**Next action:** produce **schema v0.3** folding in the ChatGPT normalizations, THEN build one
real, fully-sourced **Lead Belly** entry as the stress test (fill every `[locate]` from real
scholarship; compute a real `api_score`; emit both the `carData` JSON and the Pete-voice
article). Lead Belly is confirmed the richest first subject (44 KB harvest, ~1 MB JSON, real
scholarship: Wolfe & Lornell 1992, Lomax 1936, Santelli 2015).

## C. The Experience architecture (six worlds + interface)
**Status:** ✅ architecture documented · 🟡 interface spec returned by ChatGPT, **needs a
reconciliation pass** · 🔲 nothing built.
**What exists:** `experience-architecture.md` (six worlds, Concourse, shared grammar, three
visual registers, the image-text law, build sequence). ChatGPT returned a detailed
**Interactive Element System v0.1** (eight component families: persistent chrome, navigational
instruments, entry surfaces, callout glyphs, evidence controls, world-signature interactions,
state indicators, cross-world carriers; a full **schema→click mapping table**; a glyph audition
brief; ChatGPT-image-gen packet templates; a **ComfyUI production workflow**; a Show-001 +
Lead-Belly **first-build list** of 15 components; acceptance tests).
**Next action:** do the **reconciliation pass** (same treatment we gave the Six Worlds memo) →
produce an **"Interface Bible"**: the UI equivalent of the Framing Standard, adopting ChatGPT's
read/write split, the public `DR-GAP` rename, and the production hierarchy, and aligning its
`entry_type` / evidence vocabulary with schema v0.3. Then (visual track, separable): freeze
broad image generation, rule ~30 canonical winners across the three registers, complete the
archival-photo pipeline, build the Show-001 + Lead-Belly clickable slice.
**Pipeline (decided):** ChatGPT image-gen = audition instrument; **ComfyUI** = deterministic
production; three asset classes (scene raster / vector-code interface objects / composited
evidence). Interface objects and the five callout glyphs are **redrawn as SVG/code**, never
shipped as raster.

## D. The Reading world apparatus (Mr. Read's CURRENT focus)
**Status:** 🟡 v0.1 committed + corpus-grounded audit. He is actively reading scholarship.
**What exists:** `reading-world-apparatus.md` — **13 camps** of blues scholarship (founding
Black intelligentsia → revisionist historiography → witness literature → **camp 13 revival
practitioner-writers: Guthrie/Seeger/Dylan/Fahey**); **Fahey seated as lawgiver** (the
Koonaklaster) with Marcus as foil; **8 positionality axes** (per author-work pair, incl.
relation-to-the-money and inheritance/independence); a **declared-vs-operative purpose**
taxonomy; the **source dossier template** (with the payoff `ruling` block: `reliable_for /
unreliable_for / witness_value`); the **double-reading rule** (every source is evidence twice —
argument about its subject AND witness of its own moment; re-shelve, never burn);
independence-aware corroboration + **error genealogies**; the archive's public **self-dossier**;
and the **corpus audit** (strengths + the Priority 1–3 holes, see `03` §4).
**Next action (pick with Mr. Read):**
1. **First live dossier** — recommended opener: **Perry Bradford, *Born with the Blues*** (a
   Black primary/witness voice already in the corpus at 1,682 claims — exactly what the
   apparatus exists to center). Or dossier whatever book is open on his desk. Fill camp,
   positionality, declared-vs-operative purpose, claims-with-locators, and the ruling — the
   first real dossier will bend the template the way Lead Belly bent the entry schema.
2. **Acquisition dispatch** — turn the Priority-1 holes (`03` §4) into a rent-party-style
   sourcing lane list (*Lost Delta Found*, Calt/Wardlow Patton, late Lomax, Murray + Ellison,
   Hamilton/Miller, *Escaping the Delta*, Marcus).
3. **Ratify camps** — confirm the provisional 13-camp taxonomy by clustering across dossiers
   (open question: is *Living Blues*' editorial line a camp? Is Gussow a camp of one?).

## E. The ChatGPT thread (external collaborator)
**Status:** ⏳ active in Mr. Read's hands. Two big memos delivered and integrated; the interface
brief (`handoff-chatgpt-interface.md`) was sent and ChatGPT returned the Element System v0.1.
**Next:** if Mr. Read wants ChatGPT's take on the Reading apparatus or the Interface Bible,
prepare a delta-structured brief for it (same pattern as `handoff-chatgpt-interface.md`:
what's locked, what's new, the assignment, a Drive reading list, and an explicit invitation to
disagree — its disagreements have been the most valuable output).

---

## The single highest-leverage next move

If Mr. Read gives no specific direction, advance **D.1 — the first live source dossier** (he is
reading right now, so this meets him where he is), and in parallel note that **B (schema v0.3 +
the real Lead Belly entry)** is the move that unlocks every downstream build. Everything routes
through the entry schema; the Reading dossier is the content that fills the `reading` station
and the whole READING world.

## Complete file inventory of this work (all on the branch)

```
docs/cc-blues/
├── wiki-archive-experience.md        (three-things model + six source layers)
├── entry-schema.md                   (the entry contract, v0.2 + v0.3 deltas)
├── experience-architecture.md        (six worlds, grammar, registers, image law)
├── handoff-chatgpt-interface.md      (interface brief sent to ChatGPT)
├── reading-world-apparatus.md        (camps, positionality, dossiers, corpus audit)
└── handoff/
    ├── 00-START-HERE.md
    ├── 01-vision-and-model.md
    ├── 02-locked-canon.md
    ├── 03-drive-map-and-corpus.md
    ├── 04-environment-and-tooling.md
    └── 05-workstreams-and-next-steps.md   (this file)
```

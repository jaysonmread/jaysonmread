# CC Blues — Handoff Package: START HERE

**Prepared:** 2026-07-15 · **For:** a fresh Claude Code session with none of this conversation's context
**Repo:** `jaysonmread/jaysonmread` · **Branch:** `claude/wiki-architecture-integration-x9ytpn`
**Owner:** Mr. Read (Jayson Read, jaysonmread@gmail.com)

---

## 0. Read this first, in 60 seconds

**CC Blues is an archive of Black American music history (blues + folk), built as a
navigable "six-world" museum-railroad in the browser.** The real project lives in **Google
Drive** (`My Drive / CC Blues Archive V2`), NOT in this git repo. This repo (`jaysonmread`,
the user's GitHub profile repo) is only where we've been **scribing architecture and
strategy documents** on the branch above. Do not expect application code here.

There are **three things**, and keeping them distinct is the whole point of this project:

1. **The Foundation** (private, "for my eyes only," ~100× denser than what ships) — the
   LLM-maintained synthesis Wiki + the Vault + the Sources + the Master Database + the
   research reports. This is the source of truth everything else is generated from.
2. **The Archive** (public) — a "significantly better than Wikipedia" **text encyclopedia**
   of every show, artist, circle, scene, record, reading, and timeline.
3. **The Experience** (public, title pending) — the **same entries** rendered as a visual,
   in-browser, video-game-like world of six connected "worlds."

Key synthesis reached this cycle: **The Archive is the Experience's `READ MODE`.** They are
not two builds. One entry schema → a spatial view (Experience) and a linear cited view
(Archive). Build once, render twice.

The six worlds are **six verbs (LOCKED):**
> **RAIL assembles · RIVER carries · ROAD moves · RECORD spins · READING tells · RADIO transmits**

---

## 1. How to use this handoff package

Read the numbered files in `docs/cc-blues/handoff/` in order:

| File | What it gives you |
|---|---|
| `00-START-HERE.md` | this — orientation + doc map + first actions |
| `01-vision-and-model.md` | the full conceptual model: three things, six worlds, how it all fits |
| `02-locked-canon.md` | **every locked decision + what is BANNED** — do not relitigate these |
| `03-drive-map-and-corpus.md` | Google Drive topology with the **file/folder IDs** you'll need, and the scholarly corpus + its holes |
| `04-environment-and-tooling.md` | **operational gotchas** — Drive MCP quirks, PDF extraction, egress blocks, git flow |
| `05-workstreams-and-next-steps.md` | where each thread stands + concrete next actions |

Then the **five deep-reference docs** one level up in `docs/cc-blues/` are the primary
sources — the handoff files summarize and cross-link them, but these are authoritative:

| Doc | Subject |
|---|---|
| `wiki-archive-experience.md` | the three-things model + the six source layers of the Foundation |
| `entry-schema.md` | **the single entry contract** (v0.2 + v0.3 deltas) — matches the real `carData` |
| `experience-architecture.md` | six worlds, the Concourse, the shared interaction grammar, visual registers, image law |
| `handoff-chatgpt-interface.md` | the interface-design brief sent to Mr. Read's ChatGPT thread |
| `reading-world-apparatus.md` | **the Reading world**: camps of scholarship, positionality, source dossiers, corpus audit |

---

## 2. Who's building what (the collaboration shape)

- **Mr. Read** builds the **back-end presentation** and makes every editorial/canon call.
  Content then "trickles in piece by piece." He is currently focused on **the Reading world**
  (he is actively reading blues scholarship and wants the critical-analysis apparatus).
- **This Claude (Claude Code)** — scribes architecture, researches the Drive corpus, drafts
  schemas/specs, reconciles external input against the canon. Writes docs to the repo branch.
- **ChatGPT (a separate thread Mr. Read runs)** — has produced two major design memos that
  we integrated (see `02` and `05`). It has Google Drive access. Treat its output as strong
  peer review to reconcile, not gospel — it has been right often and wrong occasionally
  (e.g. it mislabeled the audition tool as Midjourney; it's actually ChatGPT image-gen).
- **Agent "rent party" lanes** (Cursor/Antigravity/Codex) — Mr. Read's parallel-agent
  campaigns that pour seed content into the Vault, merged by a step called "Hammer."

---

## 3. The three most important rules (violating these breaks trust)

1. **NO AI, EVER, in public output.** Deep-research reports (Gemini DR etc.) and Wikipedia
   harvests are **internal leads only** — used to *locate* the real scholarly source, then
   discarded from the record. Public citations come only from real sources. The word "AI"
   never appears publicly. No AI-generated factual text in images; no generated faces.
   (This is Mr. Read's hardest line — the project's entire credibility rests on real
   provenance, not "AI slop.")
2. **The Framing Standard governs all public language.** No "discovered/rediscovered," no
   evolutionary ladders, no "spine/substrate/foundation-for," no vibe-as-evidence. Name the
   maker, the music, the action, the evidence, and the money. See `02-locked-canon.md`.
3. **Ground everything in the actual Drive corpus, not your training data.** The registry of
   record is `sources.csv`. The last time exemplars were drawn from general knowledge
   instead of the corpus, it was (correctly) called out. Read before you assert.

---

## 4. First actions for a new session

1. Read `02-locked-canon.md` and `04-environment-and-tooling.md` completely before doing anything.
2. Confirm you're on branch `claude/wiki-architecture-integration-x9ytpn` (create from latest
   `origin/main` if the prior PR merged — see `04`).
3. Load Google Drive MCP tools via `ToolSearch` (the server ID changes between reconnects;
   search by keyword, e.g. `search_files read_file_content`).
4. Ask Mr. Read which thread he wants to advance (most likely **the Reading world** — a source
   dossier on a book he's reading, or an acquisition dispatch for the Priority-1 corpus holes).

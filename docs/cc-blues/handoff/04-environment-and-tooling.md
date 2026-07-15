# CC Blues — Environment & Tooling Gotchas

_Operational reality of this Claude Code environment. Every item here cost time to discover.
2026-07-15._

---

## 1. Git flow

- **Branch:** `claude/wiki-architecture-integration-x9ytpn`. Develop, commit, and push here.
- **Repo:** `jaysonmread/jaysonmread` — the user's **GitHub profile repo**. The CC Blues docs
  live under `docs/cc-blues/`. `README.md` at root is an unrelated profile placeholder; do not
  "fix" it. No application code is in this repo — the app lives in Google Drive / will be built
  from the entry schema later.
- **Push:** `git push -u origin claude/wiki-architecture-integration-x9ytpn`. Retry on network
  errors with backoff.
- **If the branch's PR has already merged:** treat follow-up as fresh — reset the branch from
  latest `origin/main` (`git fetch origin main && git checkout -B <branch> origin/main`) and
  push the new work; never stack on merged history.
- **Commit trailer** (used throughout this project):
  ```
  Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>
  Claude-Session: https://claude.ai/code/session_01NrWaqyELKhDmXSehmAHsYX
  ```
  (Do NOT put the model identifier or any "AI" phrasing into content pushed to CC Blues Drive
  — chat only. In commits the trailer is fine.)
- Do **not** open a PR unless Mr. Read asks.

## 2. Google Drive MCP — the important quirks

- **The server ID changes between reconnects.** It has appeared as
  `mcp__434a18f4-...__search_files` and as `mcp__Google_Drive__search_files`. It also
  disconnects mid-session and reconnects. **Always (re)load the tools via `ToolSearch`** with a
  keyword like `select:...` or `search_files read_file_content` right before you need them; do
  not assume a previously-loaded ID still resolves.
- **`search_files` query language** is structured: `title contains '...'`, `fullText contains
  '...'`, `mimeType = '...'`, `parentId = '<folderId>'`, combined with `and/or/not`. Strings
  are single-quoted. Use `parentId = '<id>'` to list a folder's children.
- **The file-title field in results is `title`, NOT `name`.** (`.name` returns null — this
  wasted a step early on.)
- **Results routinely exceed the token limit** and get spilled to a file under
  `/root/.claude/projects/.../tool-results/*.txt`. Parse those with `jq`, e.g.:
  ```bash
  jq -r '.files | sort_by(.modifiedTime) | reverse | .[] | "\(.modifiedTime[0:16])  \(.title)  \(.id)"' "$F"
  ```
  Pass `excludeContentSnippets: true` to shrink results when you only need titles/IDs.
- **`read_file_content`** returns a natural-language rendering; it works on `.md` and `.csv`
  even though the "supported mime types" list omits them. Markdown comes back with characters
  backslash-escaped (`\#`, `\-`, `\[`) — read through it.
- **Writing to Drive:** `create_file` / `copy_file` exist but were not used this cycle. Do NOT
  write into the carefully-structured Vault/Wiki without an explicit instruction and a chosen
  location (the rent-party `00-Inbox/` staging pattern is the safe convention). Scribing has
  been done in the git repo, not Drive.

## 3. ccblues.com is BLOCKED (cannot visit from this environment)

- WebFetch/curl to `ccblues.com` / `www.ccblues.com` return **403 `connect_rejected` — "gateway
  answered 403 to CONNECT (policy denial)"**. This is the **environment's egress network
  policy**, not the site and not something Claude can whitelist from inside the session.
- To enable it, **Mr. Read** must add `ccblues.com` to the environment's allowed domains in the
  Claude Code on the web settings (https://code.claude.com/docs/en/claude-code-on-the-web), or
  choose a more open network policy. Until then, learn the POC from Drive (`cc-blues-poc/`).
- Diagnose egress with: `curl -sS "$HTTPS_PROXY/__agentproxy/status"` (see `recentRelayFailures`).
  Never disable TLS verification or unset `HTTPS_PROXY`.

## 4. PDF extraction is broken — use the zlib fallback

The uploaded PDFs (e.g. ChatGPT's memos) could not be read by the normal tools:
- `Read` with `pages:` → **"pdftoppm is not installed"** (no poppler).
- `pypdf`, `PyPDF2`, `pdfminer.six` all → **`ModuleNotFoundError: _cffi_backend`** /
  cryptography rust panic. `pip install` of them does not fix it.
- **Working method: a pure-Python zlib extractor** (no deps). Find `stream…endstream`, zlib-
  decompress, regex the parenthesized text strings:
  ```python
  import zlib, re
  data = open(path,'rb').read()
  out=[]
  for m in re.finditer(rb'stream\r?\n(.*?)\r?\nendstream', data, re.S):
      try: dec = zlib.decompress(m.group(1))
      except: continue
      txt=[s.group(0)[1:-1] for s in re.finditer(rb'\((?:[^()\\]|\\.)*\)', dec)]
      if txt: out.append(b''.join(txt).decode('latin-1', 'ignore'))
  print("\n".join(out))
  ```
- The **tail of the output is embedded font data (garbage)** — filter to "readable" lines
  (>85% printable ASCII) before summarizing. Spill long output to a scratch file and `Read` it
  in chunks. This successfully extracted both ChatGPT memos.

## 5. Scratchpad & temp files

Use the session scratchpad for all temp work:
`/tmp/claude-0/-home-user-jaysonmread/d07583ef-6461-5c93-a8cf-4319b113f18e/scratchpad`
(The extracted ChatGPT-memo text was saved here as `gpt56.txt` / `gpt56_clean.txt`.)

## 6. Uploaded artifacts from this conversation

Mr. Read uploaded three files (paths under `/root/.claude/uploads/.../`):
- **ChatGPT "Six Ways the Blues Moves" memo** (PDF) — the six-worlds architecture; integrated
  into `experience-architecture.md`.
- **`CC_Blues_Interactive_Element_System_v0.1.md`** — ChatGPT's full interactive-element spec
  (eight component families, schema→click table, glyph brief, ComfyUI workflow, Show-001 +
  Lead-Belly first-build list). **Not yet fully reconciled** into our canon — see
  `05-workstreams-and-next-steps.md`. Its strongest adopted points: the read/write split
  (clicks → `ui_state`), the public renaming of `DR-GAP`, the production hierarchy.
- **`IMG_8172.png`** — screenshot of the Zone 03 Scholarly Sources Drive folder (context for
  the corpus audit).

These uploads are ephemeral to that session; a new chat won't have them. The *content* of the
first two is captured in `experience-architecture.md` and (partially) in this package. If Mr.
Read needs them again he can re-share; the ChatGPT thread still holds them.

## 7. Model note

This conversation ran mostly on Claude (identified as `claude-fable-5` for part of it, switched
to `claude-opus-4-8` at the end for this handoff). Irrelevant to the work except: the commit
trailer used "Claude Opus 4.8." Keep model identifiers out of anything pushed to CC Blues Drive.

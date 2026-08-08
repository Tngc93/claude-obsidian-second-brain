# Start here

This file has three jobs: it sets the vault up the first time, it reconfigures it later, and it tells you what to do when something is off.

**Keep this file.** It is not a one-time onboarding script — sections (b) and (c) stay useful for as long as you use the vault.

---

## (a) First-time setup

Open this folder in Claude Code and say:

> Read START-HERE.md and set up my second brain.

Claude will ask you eight questions, one at a time. It takes about five minutes. Nothing is written until the questions are done.

The first two — **what this vault is for** and **which areas you want to start with** — are yours to answer and have no defaults; they are the only things Claude cannot reasonably guess. The remaining six all have sensible defaults you can accept one by one, or wave through together once the first two are answered.

**What Claude does — instructions for Claude:**

1. Check whether `system/config.md` exists. If it does, say so and ask whether the user wants to reconfigure — do not overwrite silently.
2. Read `system/setup-interview.md` and ask its questions **one at a time**. Questions 1 and 2 (`## Purpose`, `## Focus domains`) are **mandatory with no defaults** — do not skip them, do not invent answers, and do not accept "use the defaults" in their place. Questions 3–8 have defaults; once 1 and 2 are answered, "use the defaults for the rest" is a valid answer for all six.
3. Copy `system/config.example.md`, fill in the answers, and write the result as `system/config.md` with `configured: true`. **Do not modify `config.example.md`.**
4. Verify that `.gitignore` contains `system/config.md`. Warn if it does not.
5. **Do not** translate or edit `system/templates/*`, `index.md`, or `log.md`. They stay as they are so your vault remains comparable against future template versions.
6. **Do not** create any `wiki/domains/` pages. Domain pages are written when the first real source for them arrives.
7. Append the first entry to `log.md`: `## [YYYY-MM-DD] setup | Second brain configured`, with a one-line body stating that setup completed and that personal settings live in the local, untracked `system/config.md`. **Do not write the chosen values into `log.md`** — no purpose text, no domain names, no language or autonomy settings. `log.md` is tracked by git; the configuration deliberately is not.
8. Summarize the setup in the conversation language — in the conversation, not in a file — and point the user back here for reconfiguration and troubleshooting.

**What you should do afterwards:**

- Open this folder as a vault in Obsidian
- Obsidian → Settings → Files and links → Attachment folder path: `inbox/assets`
- Read `system/PRIVACY.md` before you push this anywhere
- Drop a source into `inbox/` and say "process this"

---

## (b) Reconfiguring

Everything you chose during setup lives in `system/config.md`. Change it any time — either edit the file directly, or say:

> Update my config.

| What you want to change | Field in `system/config.md` | Effect |
|---|---|---|
| What the vault is for | **Purpose** | Changes how Claude judges whether a source deserves a page |
| Add or drop a focus area | **Focus domains** | Changes the `domain` frontmatter values and which hub pages exist |
| Language Claude talks to you in | **Conversation language** | Messages and reports |
| Language pages are written in | **Wiki language** | Page bodies and headings. File names and frontmatter stay English |
| Language Claude researches in | **Research language** | Where verification sources come from |
| How much Claude asks first | **Autonomy level** | `autonomous` / `confirm-writes` / `confirm-all` |
| What always needs approval | **Approval gates** | Applies at every autonomy level |
| How strictly claims are sourced | **Verification depth** | `strict` archives a source for every significant claim; `light` only for critical ones |

Changing the wiki language does **not** rewrite existing pages. New pages use the new language; old ones stay as they are unless you explicitly ask for a rewrite.

---

## (c) Troubleshooting

**Claude refuses to ingest and points me back here.**
Expected behavior when `system/config.md` is missing or still says `configured: false`. Run setup, or check that the file's frontmatter says `configured: true`.

**`system/config.md` is missing.**
It is gitignored on purpose, so it does not travel with a clone or a fresh checkout. Rebuild it: copy `system/config.example.md` to `system/config.md` and fill it in, or just run setup again.

**`system/config.md` is malformed and Claude misreads it.**
Compare it against `system/config.example.md` — the field names and headings should match. The most common cause is a broken YAML frontmatter block at the top.

**Claude writes pages in the wrong language.**
Check **Wiki language** in `system/config.md`. Remember that file names, frontmatter field names, frontmatter enum values, callout types, and `log.md` entry types are always English by design — that is not a bug.

**Claude stopped mid-ingest and is asking about `inbox/`.**
`inbox/` takes one source at a time plus its images. With more than one source, an image in `inbox/assets/` cannot be matched to its owner with certainty, so Claude asks instead of guessing. Tell it which source to process first.

**Obsidian's graph is full of nodes I did not write.**
Expected. Obsidian's global Graph view shows **every markdown note in the vault** by default — that includes `README.md`, `CLAUDE.md`, `START-HERE.md`, the files under `system/`, and all nine page templates. They are outside the wiki *content* layer, but they are still markdown files in the vault, so the graph draws them.

Filter the graph to see only real wiki pages: **Graph view → Filters → Search files**, then type `path:wiki`.

**With the `path:wiki` filter my graph is empty.**
Correct for a fresh vault: `wiki/` genuinely starts empty. It fills as sources get processed. If the graph is still empty after an ingest, check that pages were actually written under `wiki/` and run a lint.

**A citation links to a raw file that is not there.**
Run a lint — say "lint" — and Claude reports broken raw-file paths along with other integrity problems.

**I updated to a newer template version and something behaves differently.**
Check three things in order: `CLAUDE.md` (the schema itself), `system/config.example.md` against your `system/config.md` (new fields are not migrated automatically), and `system/templates/*`. See the README section on updating.

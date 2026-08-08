# Setup interview

The canonical question list for first-time setup. Claude reads this file, asks the questions one at a time, and writes the answers into `system/config.md`.

**Instructions for Claude:**

- Ask **one question at a time**, in the order below.
- **Questions 1 and 2 are mandatory and have no defaults.** They cannot be skipped, defaulted, or guessed. If the user asks to "just use the defaults" before answering them, explain that purpose and focus domains are the two things only they can supply, ask them again, and continue only once both are answered.
- Questions 3–8 all have defaults. Offer the default with each one. Once questions 1 and 2 are answered, the user may say "use the defaults for the rest" — then fill the remaining six with their defaults and continue.
- Ask questions 1–3 in English unless the user has already written to you in another language; from the moment the conversation language is set, use it.
- Write the result to `system/config.md` by copying `system/config.example.md` and filling it in. Set `configured: true`. **Do not modify `config.example.md`.**
- Do not translate or edit `system/templates/*`, `index.md`, or `log.md`.
- Do not create any `wiki/domains/` pages — they are written when the first real source arrives.
- Never ask for the user's real name, email address, or any other personal identifier. None of it is needed and none of it belongs in this vault.

---

## 1. Purpose — **mandatory, no default**

**Ask:** What is this second brain for? In two or three sentences — what kind of knowledge should accumulate here, and what should it help you do later?

**Why:** This is what separates a knowledge base from a pile of notes. Claude uses it to judge whether a given source is worth a page at all.

**Default:** **none.** Do not proceed without an answer, and do not invent one. Writes to `## Purpose`.

## 2. Focus domains — **mandatory, no default**

**Ask:** Which two to four areas do you want to start with? For each, give a short name and a one-line scope.

**Why:** Domains become the `domain` frontmatter value and the hub pages under `wiki/domains/`. Starting with a few concrete areas beats starting with everything.

**Note to the user:** this is a starting focus, not a closed set. When something falls outside, Claude proposes a new domain rather than forcing a bad fit.

**Default:** **none.** Do not proceed without an answer, and do not invent domains. Two or three is a good number; more than four early on tends to fragment. Writes to `## Focus domains`.

## 3. Conversation language

**Ask:** Which language should I talk to you in?

**Why:** Every message and every report uses this.

**Default:** `English`

## 4. Wiki language

**Ask:** Which language should the wiki pages themselves be written in? It can differ from the conversation language.

**Why:** Page bodies, headings, summaries, and syntheses use this. File names and frontmatter field names stay English regardless, so the schema stays portable.

**Default:** same as the conversation language.

## 5. Research language

**Ask:** Which language should I search and verify in?

**Why:** For most technical and academic subjects, the primary sources are in English even when you prefer to read summaries in another language. Keeping this separate lets you have both.

**Default:** `English (primary sources preferred)`

## 6. Autonomy level

**Ask:** How should I work — do maintenance on my own and report afterwards, check with you before writing pages, or ask before every file operation?

**Why:** Determines whether routine ingest work stops for approval. The approval gate in question 7 applies regardless of what you pick here.

**Default:** `autonomous` (do it, then report)

## 7. Approval gates

**Ask:** These always require your approval first, at every autonomy level. Do you want to add anything?

Show the default list from `config.example.md`.

**Why:** These are the operations that are hard to undo or that leave the vault.

**Default:** the list as-is.

## 8. Verification depth

**Ask:** Should every significant claim be tied to an archived source, or only the critical ones?

**Why:** `strict` is slower and produces a much more trustworthy wiki, because every verification source gets downloaded and archived. `light` is faster and leaves more claims resting on the original source alone.

**Default:** `strict`

---

## Where each answer goes

Section names must match `system/config.example.md` and `CLAUDE.md` §0 exactly.

| Question | Section in `system/config.md` | Default |
|---|---|---|
| 1 | `## Purpose` | **none — mandatory** |
| 2 | `## Focus domains` | **none — mandatory** |
| 3 | `## Conversation language` | `English` |
| 4 | `## Wiki language` | same as conversation language |
| 5 | `## Research language` | `English (primary sources preferred)` |
| 6 | `## Autonomy level` | `autonomous` |
| 7 | `## Approval gates` | the default list |
| 8 | `## Verification depth` | `strict` |

Three sections are **not asked about** and simply keep their documented defaults: `## Scope boundary`, `## Terminology rule`, `## Git policy`. Mention them in the summary so the user knows they exist and can be edited.

---

## After the interview

1. Write `system/config.md` with `configured: true`.
2. Confirm that `.gitignore` contains `system/config.md`; warn the user if it does not.
3. Append the first entry to `log.md`, exactly this shape:

   ```markdown
   ## [YYYY-MM-DD] setup | Second brain configured

   Setup completed. Personal settings are kept in the local, untracked `system/config.md`.
   ```

   The heading format stays English; the body sentence is written in the wiki language.

   **Do not summarize the answers in `log.md`.** No purpose text, no domain names, no language settings, no autonomy or verification values. `log.md` is tracked by git and may end up somewhere public; the configuration deliberately is not. The log records *that* setup happened, never *what was chosen*.
4. Summarize the setup **for the user, in the conversation** — that summary is fine and useful. It just does not get written to a file.
5. Tell them `START-HERE.md` stays in the repo — it is also the reconfiguration and troubleshooting guide.

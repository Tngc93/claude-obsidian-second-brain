# Porting improvements upstream

**Who this is for:** the maintainer of this template, who also runs a personal vault built on the same schema and occasionally improves it there first.

**If you are using the template**, you do not need this file. See the "Updating to a newer template version" section in the README instead.

---

A personal vault and a public template are two different things that happen to share a schema. Improvements flow from one to the other by being **rewritten**, never by being copied. There is no sync script and there never will be — the whole risk here is that an automated copy carries something personal along with it.

## Allowlist — may be ported, still reviewed line by line

- Rule changes in `CLAUDE.md` §1–§11 — the schema itself, minus any personal examples
- Structural improvements to `system/templates/*` — new sections, new frontmatter fields, better wording. Translated to English
- `.gitignore` patterns
- General usage explanations in the README
- A new page type or a new flow (for example, an additional lint check)
- A new configuration field → added to `config.example.md`, `setup-interview.md`, and its use site in `CLAUDE.md` together; bump `config_schema_version`

## Denylist — never ported, under any circumstance

- `raw/`, `wiki/`, `inbox/` — any file
- `index.md`, `log.md` — any line
- `system/config.md` — personal preferences (gitignored anyway)
- `.obsidian/`
- Personal focus domains, project names, people or organization names, absolute paths, email addresses, local usernames
- Any text from the personal vault in its original language — it enters the template only by being rewritten in English

## Process

1. Make the improvement in the personal vault and live with it for a while. Ideas that survive contact with real use are the only ones worth porting.
2. Check the allowlist. If it is not on it, stop.
3. **Rewrite** the change in the template's context — generalize, do not copy. Strip personal examples. If something belongs in configuration rather than in the schema, turn it into a `config.example.md` field.
4. Read `git diff` line by line in the template repository.
5. Run the pre-commit scans on staged content only:
   ```
   git add -A
   git diff --cached --name-only
   git grep --cached -nIE '<personal-identifier-patterns>'
   ```
   Scan for concrete email addresses, absolute paths, local usernames, and the repository owner's identity values. Do **not** grep for the generic words `author` or `name` — `source-metadata.md` legitimately carries an `authors:` field for third-party bibliographic data, and a blanket search would flag it.
6. Commit and push. Tag or cut a release for meaningful changes, so template users have something to diff against.

## The other direction

Porting template improvements back into the personal vault follows the same discipline, with the denylist still in force. The personal vault's own configuration and focus domains are preserved.

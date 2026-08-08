---
configured: false
config_schema_version: 1
---

# Configuration

This is the **reference copy**, tracked in git. Your real settings live in `system/config.md`, which is gitignored and never committed.

`START-HERE.md` walks you through creating `system/config.md` from this file. You can also copy it by hand and fill it in.

When a newer version of the template ships, compare this file against your `system/config.md` and add any new sections yourself. There is no automatic migration; `config_schema_version` tells you when the section list changed.

**Each setting is a `##` section, and the headings below are the exact names Claude looks for** (`CLAUDE.md` §0 lists the same names). Renaming a heading makes that setting invisible.

`## Purpose` and `## Focus domains` are **mandatory and have no defaults** — setup will not proceed without them. Every other section falls back to the default documented under it.

---

## Purpose

**Mandatory. No default.**

*Two or three sentences: what is this second brain for? What kind of knowledge should accumulate here, and what should it help you do later?*

NOT CONFIGURED

## Scope boundary

What goes in, what stays out.

Default: a project's actual code, files, and day-to-day task tracking stay in that project's own folder. Only knowledge that is reusable across contexts enters here — decisions, lessons, research, methods, concepts, sources, connections.

Decision test: **"Will this still be useful to me in six months, in a different context?"** If no, it does not belong here.

## Focus domains

**Mandatory. No default.**

The `domain` frontmatter values and the page names under `wiki/domains/`. Use `kebab-case` slugs.

This is a **starting focus, not a closed set.** When a source falls outside these, Claude proposes a new domain and explains why in its report. Overlap between domains is expected; bridges live in `wiki/syntheses/`.

| `domain` slug | Scope | Also known as |
|---|---|---|
| NOT CONFIGURED | | |

## Conversation language

The language Claude talks to you in — every message and every report.

Default: `English`

## Wiki language

The language of page bodies, headings, summaries, syntheses, and lint reports.

File names, frontmatter field names, frontmatter enum values, callout types, and `log.md` entry types stay English regardless — see `CLAUDE.md` §5.

Default: `English`

## Research language

The language Claude searches and verifies in.

Default: `English (primary sources preferred)`

## Terminology rule

Default: keep established technical terms in their original form, with a short gloss in the wiki language on first use. Original source titles and direct quotes stay in their original language.

## Autonomy level

One of:

- `autonomous` — Claude does normal wiki maintenance without asking, then reports
- `confirm-writes` — Claude asks before creating or substantially rewriting any page
- `confirm-all` — Claude asks before every file operation

Default: `autonomous`

## Approval gates

Always require approval first, at every autonomy level. Add or remove entries as you like.

- Deleting, renaming, or altering anything under `raw/`
- Bulk deletion or restructuring of many pages
- Changing `CLAUDE.md`, `system/config.md`, or the core schema
- Writing files outside this vault
- Sending any data to an external service
- `git commit` / `push` / remote sync
- Anything hard to reverse or destructive

## Verification depth

- `strict` — every significant claim is tied to an archived source
- `light` — only critical claims are

Default: `strict`

## Git policy

Default: `never auto-commit or push`

Claude will not run git commands that change state unless you ask, and asks first even then.

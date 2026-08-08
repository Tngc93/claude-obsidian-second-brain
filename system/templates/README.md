# Page templates

Wiki pages follow these skeletons. **These are structural references, not text to copy.** They live outside `wiki/` — they are reference material, not part of the wiki content layer — and they contain no `[[wikilinks]]`.

Note that "outside `wiki/`" is not the same as "invisible in Obsidian". Obsidian's global Graph view shows **every markdown note in the vault** by default, so these template files appear there too, as unlinked nodes. To see only real wiki pages, filter the graph with `path:wiki` — see the README.

| Template | Used for |
|---|---|
| `domain.md` | A domain hub page — the entry point to everything in that domain |
| `concept.md` | A concept, method, or mental model |
| `entity.md` | A person, organization, tool, product, or project |
| `decision.md` | A decision that was made, with rationale and outcome |
| `lesson.md` | A lesson learned, a recurring pattern |
| `source.md` | The summary page for one raw source (`wiki/sources/`) |
| `synthesis.md` | Cross-domain synthesis, comparison, durable query output |
| `source-metadata.md` | For `raw/<id>/metadata.md` |

## Language rule

**These files stay in English and are never translated or edited in place.**

When Claude writes an actual wiki page it follows the section order and frontmatter fields shown here, but writes **headings and body text in the wiki language** set in `system/config.md`.

Always English, in every language setting:

- File names (`kebab-case.md`) and folder names
- Frontmatter **field names** — `type`, `domain`, `created`, `updated`, `sources`, `status`, `tags`, `role`, `verifies`, …
- Frontmatter **enum values** — `concept`, `entity`, `decision`, `lesson`, `source`, `domain`, `synthesis`, `draft`, `active`, `needs-review`, `primary`, `verification`
- Callout types — `[!inference]`, `[!question]`, `[!warning]`
- `log.md` entry types — `setup`, `ingest`, `query`, `lint`, `refactor`

This keeps the schema portable across languages and keeps your vault comparable against future versions of the template.

## Shared rules

Full rules live in `CLAUDE.md` §5 and §6. In short: inline citations are required, anything not directly in a source is tagged `[!inference]` or `[!question]`, contradictions never silently delete the older claim, and links are only created where they are meaningful.

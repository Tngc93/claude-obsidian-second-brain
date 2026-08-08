# Log

Chronological, append-only. New entries go at the **bottom**.

Format: `## [YYYY-MM-DD] type | Title`

Type is one of `setup` | `ingest` | `query` | `lint` | `refactor`, always in English so the log stays greppable. Entry titles and bodies are written in your wiki language.

Last five entries: `grep "^## \[" log.md | tail -5`

---

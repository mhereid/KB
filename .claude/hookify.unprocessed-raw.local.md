---
name: warn-unprocessed-raw
enabled: true
event: file
conditions:
  - field: file_path
    operator: regex_match
    pattern: /raw/.*\.md$
---

A raw source file was just created or modified in a `raw/` directory.

**Action needed:** Run `/process-raw` to generate or update wiki articles from this source. Raw files are not visible on the KB frontend until they are processed into wiki articles.

The `/process-raw` skill will:
1. Read the raw source
2. Generate a wiki article with proper formatting, cross-links, and source references
3. Update INDEX.md
4. Commit and push (triggering auto-deploy to hereid.co/kb)

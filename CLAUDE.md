# Knowledge Base Schema

## What This Is
A personal knowledge base maintained by Mike Hereid, split into two domains: **personal** and **work**. Each domain has its own sources, wiki, outputs, and schema.

## Structure
```
kb/
  personal/          Personal life, hobbies, family, health, finance
    raw/
    wiki/
    outputs/
    CLAUDE.md
  work/              Professional, engineering, business, cloud
    raw/
    wiki/
    outputs/
    CLAUDE.md
```

## Shared Rules
These rules apply to both domains:

### Wiki Rules
- Every topic gets its own `.md` file in `wiki/`
- Every wiki file starts with a one-paragraph summary
- Link related topics using `[[topic-name]]` format
- Maintain an `INDEX.md` in each `wiki/` that lists every topic with a one-line description
- When new raw sources are added, update the relevant wiki articles
- Include source references back to `raw/` using `[source](../raw/filename.md)`
- Keep summaries concise but comprehensive
- Flag contradictions between sources

### Cross-Domain Rules
- Keep personal and work content strictly separated
- When a topic spans both domains (e.g., "AWS certification" is personal development but also work-relevant), place it in the primary domain and add a cross-reference note: `See also: ../work/wiki/topic.md` or `See also: ../personal/wiki/topic.md`
- Never mix personal details into work articles or vice versa

### Health Check Protocol (Monthly)
When asked to run a health check on either or both domains:
1. Review the entire `wiki/` directory for that domain
2. Flag contradictions between articles
3. Find topics mentioned but never explained
4. List claims not backed by a source in `raw/`
5. Suggest 3-5 new articles that would fill gaps
6. Check for stale or outdated information
7. Verify no cross-domain contamination

# Personal Knowledge Base Systems

A personal knowledge base (PKB) is an AI-maintained repository of your collected knowledge, organized as flat markdown files in a simple folder structure. The system uses three directories (raw sources, AI-compiled wiki, generated outputs) and a single schema file to create a compounding knowledge loop where every question makes future answers better.

## Origin

Andrej Karpathy popularized this approach in a viral post (41K+ bookmarks) describing how he uses AI to build and maintain personal knowledge bases. Nick Spisak (@NickSpisak_) expanded on the method with practical implementation details. [source](../raw/karpathy-second-brain-system.md)

## Core Architecture

```
my-knowledge-base/
  raw/          -- unprocessed source material (never modify)
  wiki/         -- AI-maintained organized articles
  outputs/      -- generated reports and answers
  CLAUDE.md     -- schema file (the AI's instruction manual)
```

## The Compounding Loop

1. **Collect** -- dump articles, notes, screenshots into `raw/`
2. **Compile** -- AI reads raw sources, writes organized wiki articles
3. **Query** -- ask questions against the wiki, get grounded answers
4. **Save** -- store answers in `outputs/` or update wiki articles
5. **Repeat** -- each cycle makes the next answer better

## Schema File

The schema file (CLAUDE.md, AGENTS.md, or README.md) tells the AI:
- What the knowledge base covers
- How to organize content (one file per topic, summaries, cross-links)
- Rules for maintaining the wiki (INDEX.md, source references)
- Your focus areas and interests

Karpathy keeps his schema "super simple and flat."

## Monthly Health Check

Critical for preventing error compounding. When AI outputs get filed back, mistakes compound. The fix:
- Flag contradictions between articles
- Find topics mentioned but never explained
- List claims not backed by raw sources
- Suggest gap-filling articles

## Related Topics
- [[flat-file-architecture]]
- [[ai-powered-web-scraping]]
- [[claude-code-workflows]]

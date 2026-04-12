# Personal Knowledge Base Systems

A personal knowledge base (PKB) is an AI-maintained repository of your collected knowledge, organized as flat markdown files in a simple folder structure. Instead of RAG (re-deriving knowledge from raw documents on every query), the LLM incrementally builds and maintains a persistent wiki — a structured, interlinked collection of markdown files that compounds over time. The wiki is a persistent, compounding artifact: cross-references are already there, contradictions already flagged, synthesis already reflects everything you've read.

## Origin

Andrej Karpathy published the "LLM Wiki" pattern describing how to use LLM agents to build and maintain personal knowledge bases. [source](../raw/karpathy-llm-wiki-gist.md) Nick Spisak (@NickSpisak_) expanded on the method with practical implementation details. [source](../raw/karpathy-second-brain-system.md) @defileo published a viral walkthrough pairing Claude Code with Obsidian as a practical "second brain" implementation of the same pattern, including daily operations (ingest, query, lint, morning briefings) and cron-based automation. [source](../../personal/raw/claude-obsidian-second-brain-defileo.md)

## Why Not RAG

Most LLM-document workflows are RAG: upload files, retrieve chunks at query time, generate an answer. The LLM rediscovers knowledge from scratch every time. Ask a subtle question requiring synthesis of five documents and it has to find and piece together fragments on every query. Nothing is built up. NotebookLM, ChatGPT file uploads, and most RAG systems work this way.

The LLM Wiki approach compiles knowledge once and keeps it current, rather than re-deriving on every query.

## Three-Layer Architecture

```
my-knowledge-base/
  raw/          -- immutable source material (articles, papers, images, data)
  wiki/         -- AI-maintained organized articles (LLM owns this layer)
  outputs/      -- generated reports, answers, briefings
  CLAUDE.md     -- schema file (conventions, workflows, structure)
```

**Raw sources** — curated, immutable. The LLM reads but never modifies. This is the source of truth.

**The wiki** — LLM-generated markdown files: summaries, entity pages, concept pages, comparisons, synthesis. The LLM creates, updates, and maintains cross-references.

**The schema** — the configuration file (CLAUDE.md, AGENTS.md) that tells the LLM how the wiki is structured, what conventions to follow, and what workflows to run. You and the LLM co-evolve this over time. Karpathy keeps his "super simple and flat."

## Core Operations

### Ingest
Drop a new source into raw/ and tell the LLM to process it. The LLM reads the source, discusses key takeaways, writes a summary page, updates the index, and updates relevant entity/concept pages across the wiki. A single source might touch 10-15 wiki pages. Karpathy prefers to ingest one at a time and stay involved — reading summaries, checking updates, guiding emphasis.

### Query
Ask questions against the wiki. The LLM searches for relevant pages, reads them, synthesizes answers with citations. Answers can take different forms: markdown page, comparison table, slide deck (Marp), chart (matplotlib), canvas. **Good answers can be filed back into the wiki as new pages** — explorations compound just like ingested sources do.

### Lint (Health Check)
Periodically health-check the wiki:
- Contradictions between pages
- Stale claims superseded by newer sources
- Orphan pages with no inbound links
- Important concepts mentioned but lacking their own page
- Missing cross-references
- Data gaps that could be filled with a web search
- The LLM suggests new questions to investigate and new sources to look for

## Indexing and Logging

**index.md** — content-oriented catalog of the wiki. Each page listed with link, one-line summary, optional metadata. Organized by category. LLM updates on every ingest. LLM reads the index first to find relevant pages, then drills in. Works at moderate scale (~100 sources, ~hundreds of pages) without embedding-based RAG infrastructure.

**log.md** — chronological, append-only record of ingests, queries, lint passes. Use consistent parseable prefixes (e.g. `## [2026-04-02] ingest | Article Title`) so it works with unix tools. Gives timeline of wiki evolution and helps the LLM understand recent activity.

## The Compounding Loop

1. **Collect** — dump articles, notes, screenshots into `raw/`
2. **Compile** — AI reads raw sources, writes organized wiki articles
3. **Query** — ask questions against the wiki, get grounded answers
4. **Save** — store answers in `outputs/` or update wiki articles
5. **Repeat** — each cycle makes the next answer better

## Use Cases

- **Personal**: goals, health, psychology, self-improvement, journal entries, podcast notes
- **Research**: deep dives over weeks or months — papers, articles, reports with evolving thesis
- **Reading a book**: chapter-by-chapter wiki with characters, themes, plot threads (think fan wikis like Tolkien Gateway)
- **Business/team**: internal wiki fed by Slack threads, meeting transcripts, customer calls, with humans reviewing updates
- **Competitive analysis, due diligence, trip planning, course notes, hobby deep-dives**

## Tooling

### Recommended
- **Obsidian Web Clipper** — browser extension to convert web articles to markdown
- **Obsidian graph view** — visualize wiki shape, connections, hubs, orphans
- **qmd** — local markdown search engine with hybrid BM25/vector search and LLM re-ranking (CLI + MCP server)
- **Marp** — markdown-based slide decks, Obsidian plugin available
- **Dataview** — Obsidian plugin for queries over YAML frontmatter

### The Anti-Pattern
"Obsidian with 47 plugins is the Notion trap all over again." Tool choice doesn't matter — flat files and a good schema outperform fancy tool stacks. See [[flat-file-architecture]].

## Why This Works

The tedious part of maintaining a knowledge base is not the reading or the thinking — it's the bookkeeping. Humans abandon wikis because the maintenance burden grows faster than the value. LLMs don't get bored, don't forget to update a cross-reference, and can touch 15 files in one pass. The human curates sources, directs analysis, asks good questions, and thinks about what it all means. The LLM does everything else.

Related in spirit to Vannevar Bush's Memex (1945) — a personal, curated knowledge store with associative trails between documents. The part Bush couldn't solve was who does the maintenance.

## Related Topics
- [[flat-file-architecture]]
- [[ai-powered-web-scraping]]
- [[claude-code-workflows]]

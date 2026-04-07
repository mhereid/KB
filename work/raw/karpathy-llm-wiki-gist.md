# LLM Wiki - Andrej Karpathy

**Source**: https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f
**Retrieved**: 2026-04-06

## The core idea

Most people's experience with LLMs and documents looks like RAG: you upload a collection of files, the LLM retrieves relevant chunks at query time, and generates an answer. This works, but the LLM is rediscovering knowledge from scratch on every question. There's no accumulation. Ask a subtle question that requires synthesizing five documents, and the LLM has to find and piece together the relevant fragments every time. Nothing is built up. NotebookLM, ChatGPT file uploads, and most RAG systems work this way.

The idea here is different. Instead of just retrieving from raw documents at query time, the LLM **incrementally builds and maintains a persistent wiki** — a structured, interlinked collection of markdown files that sits between you and the raw sources. When you add a new source, the LLM doesn't just index it for later retrieval. It reads it, extracts the key information, and integrates it into the existing wiki — updating entity pages, revising topic summaries, noting where new data contradicts old claims, strengthening or challenging the evolving synthesis. The knowledge is compiled once and then *kept current*, not re-derived on every query.

This is the key difference: **the wiki is a persistent, compounding artifact.** The cross-references are already there. The contradictions have already been flagged. The synthesis already reflects everything you've read. The wiki keeps getting richer with every source you add and every question you ask.

You never (or rarely) write the wiki yourself — the LLM writes and maintains all of it. You're in charge of sourcing, exploration, and asking the right questions. The LLM does all the grunt work — the summarizing, cross-referencing, filing, and bookkeeping that makes a knowledge base actually useful over time. In practice, I have the LLM agent open on one side and Obsidian open on the other. The LLM makes edits based on our conversation, and I browse the results in real time — following links, checking the graph view, reading the updated pages. Obsidian is the IDE; the LLM is the programmer; the wiki is the codebase.

### Use Cases
- **Personal**: tracking goals, health, psychology, self-improvement — filing journal entries, articles, podcast notes
- **Research**: going deep on a topic over weeks or months — reading papers, articles, reports
- **Reading a book**: filing each chapter, building out pages for characters, themes, plot threads
- **Business/team**: internal wiki maintained by LLMs, fed by Slack threads, meeting transcripts, project documents, customer calls
- **Competitive analysis, due diligence, trip planning, course notes, hobby deep-dives**

## Architecture

Three layers:

**Raw sources** — curated collection of source documents. Articles, papers, images, data files. Immutable — the LLM reads from them but never modifies them. Source of truth.

**The wiki** — directory of LLM-generated markdown files. Summaries, entity pages, concept pages, comparisons, overview, synthesis. The LLM owns this layer entirely.

**The schema** — a document (e.g. CLAUDE.md for Claude Code or AGENTS.md for Codex) that tells the LLM how the wiki is structured, what the conventions are, and what workflows to follow. You and the LLM co-evolve this over time.

## Operations

**Ingest.** Drop a new source into raw and tell the LLM to process it. LLM reads the source, discusses key takeaways, writes a summary page, updates index, updates relevant entity and concept pages. A single source might touch 10-15 wiki pages. Karpathy prefers to ingest one at a time and stay involved.

**Query.** Ask questions against the wiki. LLM searches relevant pages, reads them, synthesizes answers with citations. Answers can take different forms: markdown page, comparison table, slide deck (Marp), chart (matplotlib), canvas. **Good answers can be filed back into the wiki as new pages.** Explorations compound just like ingested sources do.

**Lint.** Periodically health-check the wiki. Look for: contradictions between pages, stale claims that newer sources have superseded, orphan pages with no inbound links, important concepts mentioned but lacking their own page, missing cross-references, data gaps that could be filled with a web search. The LLM suggests new questions and sources.

## Indexing and Logging

**index.md** — content-oriented catalog of everything in the wiki. Each page listed with link, one-line summary, optional metadata. Organized by category. LLM updates it on every ingest. LLM reads index first to find relevant pages. Works well at moderate scale (~100 sources, ~hundreds of pages) without embedding-based RAG.

**log.md** — chronological append-only record. Ingests, queries, lint passes. Parseable with consistent prefixes (e.g. `## [2026-04-02] ingest | Article Title`). Gives timeline of wiki evolution, helps LLM understand recent activity.

## Optional: CLI Tools

At scale you may want search beyond the index. [qmd](https://github.com/tobi/qmd) is a local search engine for markdown files with hybrid BM25/vector search and LLM re-ranking, all on-device. Has CLI and MCP server.

## Tips and Tricks

- **Obsidian Web Clipper** — browser extension to convert web articles to markdown for raw/
- **Download images locally** — in Obsidian settings, set attachment folder to `raw/assets/`, bind a hotkey for "Download attachments for current file"
- **Obsidian graph view** — best way to see wiki shape, connections, hubs, orphans
- **Marp** — markdown-based slide deck format, Obsidian has a plugin
- **Dataview** — Obsidian plugin for queries over page frontmatter (YAML tags, dates, source counts)
- The wiki is just a git repo of markdown files — version history, branching, collaboration for free

## Why This Works

The tedious part of maintaining a knowledge base is not the reading or the thinking — it's the bookkeeping. Updating cross-references, keeping summaries current, noting when new data contradicts old claims, maintaining consistency across dozens of pages. Humans abandon wikis because the maintenance burden grows faster than the value. LLMs don't get bored, don't forget to update a cross-reference, and can touch 15 files in one pass.

The human's job is to curate sources, direct the analysis, ask good questions, and think about what it all means. The LLM's job is everything else.

Related to Vannevar Bush's Memex (1945) — a personal, curated knowledge store with associative trails between documents. The part Bush couldn't solve was who does the maintenance. The LLM handles that.

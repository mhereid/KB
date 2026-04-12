# Claude Code Workflows

Claude Code is a terminal-based AI coding assistant that can read, write, and manage files across entire project directories. It's particularly well-suited for maintaining knowledge bases, automating development workflows, and orchestrating multi-file operations.

## Knowledge Base Management

Claude Code can serve as the primary tool for maintaining a [[personal-knowledge-base-systems|personal knowledge base]]:
- Read all files in `raw/` and compile organized wiki articles
- Maintain cross-references and an INDEX.md
- Run health checks to catch contradictions and gaps
- Generate reports and briefings from collected knowledge

## Key Patterns

### Schema-Driven Behavior
Place a `CLAUDE.md` file in your project root to define:
- Project structure and conventions
- Rules for how AI should organize content
- Focus areas and priorities

### The Three Operations (from Karpathy's LLM Wiki)
- **Ingest**: Process a new source — write summary, update index, update 10-15 related wiki pages in one pass
- **Query**: Search wiki for relevant pages, synthesize answers with citations. File good answers back as new wiki pages.
- **Lint**: Health-check for contradictions, stale claims, orphan pages, missing cross-references, data gaps

### Prompt Patterns for Knowledge Work
- **Compile**: "Read everything in raw/. Compile a wiki following CLAUDE.md rules."
- **Query**: "Based on wiki/, what are the gaps in my understanding of [topic]?"
- **Compare**: "Where do source A and source B disagree about [concept]?"
- **Brief**: "Write a 500-word briefing on [topic] using only this knowledge base."
- **Health check**: "Review wiki/. Flag contradictions, unexplained topics, unsourced claims."

### Indexing and Logging
- **index.md**: Content-oriented catalog updated on every ingest. LLM reads it first to find relevant pages — works at moderate scale without embedding-based RAG.
- **log.md**: Chronological append-only record with parseable prefixes (e.g. `## [2026-04-02] ingest | Article Title`). Gives timeline of wiki evolution.

## Plugins & Skills
Claude Code supports an extensible plugin system for specialized workflows:
- **feature-dev** -- guided feature development with codebase exploration
- **hookify** -- create enforcement rules from conversation analysis
- **ralph-loop** -- autonomous iteration loops with completion conditions
- **skill-creator** -- build and test custom skills

## Related Topics
- [[personal-knowledge-base-systems]]
- [[flat-file-architecture]]
- [[claude-managed-agents]]
- [[agent-harness-hill-climbing]]

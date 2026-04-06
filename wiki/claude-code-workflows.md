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

### Prompt Patterns for Knowledge Work
- **Compile**: "Read everything in raw/. Compile a wiki following CLAUDE.md rules."
- **Query**: "Based on wiki/, what are the gaps in my understanding of [topic]?"
- **Compare**: "Where do source A and source B disagree about [concept]?"
- **Brief**: "Write a 500-word briefing on [topic] using only this knowledge base."
- **Health check**: "Review wiki/. Flag contradictions, unexplained topics, unsourced claims."

## Plugins & Skills
Claude Code supports an extensible plugin system for specialized workflows:
- **feature-dev** -- guided feature development with codebase exploration
- **hookify** -- create enforcement rules from conversation analysis
- **ralph-loop** -- autonomous iteration loops with completion conditions
- **skill-creator** -- build and test custom skills

## Related Topics
- [[personal-knowledge-base-systems]]
- [[flat-file-architecture]]

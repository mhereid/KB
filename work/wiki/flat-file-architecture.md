# Flat File Architecture

Flat file architecture is a design philosophy that uses plain text files in simple directory structures instead of databases, specialized apps, or complex tooling. For knowledge management and many development workflows, this approach consistently outperforms more sophisticated alternatives.

## Core Principle

As Andrej Karpathy put it: "I'm trying to keep it super simple and flat. It's just a nested directory of .md files." [source](../raw/karpathy-second-brain-system.md)

## Why Flat Files Win

1. **No vendor lock-in** -- markdown files work everywhere, forever
2. **AI-friendly** -- LLMs read and write text files natively
3. **Version controllable** -- git tracks every change with full history
4. **Zero configuration** -- no plugins, no accounts, no setup
5. **Portable** -- copy a folder, move to any machine
6. **Searchable** -- grep, ripgrep, or AI search across all content instantly

## The Notion/Obsidian Trap

"Obsidian with 47 plugins is the Notion trap all over again. You spend more time configuring the tool than using the knowledge base."

Signs you've fallen into the tool trap:
- More time configuring than creating
- Plugin conflicts and update anxiety
- Can't access content without the specific app
- Migration dread when a better tool appears

## When Flat Files Are Enough
- Personal knowledge bases
- Documentation
- Note-taking systems
- Project planning
- Content pipelines

## When You Need More
- Multi-user real-time collaboration
- Complex relational queries
- Binary asset management at scale

## Related Topics
- [[personal-knowledge-base-systems]]
- [[claude-code-workflows]]

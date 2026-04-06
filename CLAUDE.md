# Knowledge Base Schema

## What This Is
A personal knowledge base maintained by Mike Hereid covering AI & LLMs, Software Engineering, Business & E-commerce, and Cloud Architecture.

## How It's Organized
- `raw/` contains unprocessed source material (articles, notes, screenshots, PDFs). Never modify these files.
- `wiki/` contains the organized wiki. AI maintains this entirely.
- `outputs/` contains generated reports, answers, analyses, and research.

## Wiki Rules
- Every topic gets its own `.md` file in `wiki/`
- Every wiki file starts with a one-paragraph summary
- Link related topics using `[[topic-name]]` format
- Maintain an `INDEX.md` in `wiki/` that lists every topic with a one-line description
- When new raw sources are added, update the relevant wiki articles
- Include source references back to files in `raw/` using `[source](../raw/filename.md)`
- Keep summaries concise but comprehensive
- Flag contradictions between sources

## My Interests
- AI tools, agents, prompting strategies, Claude Code, LLM workflows
- Software engineering best practices, architecture patterns, DevOps
- Business strategy, e-commerce growth, operations
- AWS cloud architecture, serverless, infrastructure as code

## Health Check Protocol (Monthly)
When asked to run a health check:
1. Review the entire `wiki/` directory
2. Flag contradictions between articles
3. Find topics mentioned but never explained
4. List claims not backed by a source in `raw/`
5. Suggest 3-5 new articles that would fill gaps
6. Check for stale or outdated information

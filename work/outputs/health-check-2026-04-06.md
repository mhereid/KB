# Work KB Health Check — 2026-04-06

## Summary
The work wiki has four solid, well-interlinked articles covering AI & LLMs and Software Engineering. Cross-links between articles are internally consistent and all raw files are referenced. The main issues are: several unsourced claims across multiple articles, a Notion/Obsidian trap quote that appears without attribution in two places, and three interest categories (Business & E-commerce, Cloud Architecture, Customer Success) with zero articles despite being listed focus areas.

## Contradictions
None found. The four wiki articles are mutually consistent and align with their raw sources. One note:

- `flat-file-architecture.md` and `personal-knowledge-base-systems.md` both quote "Obsidian with 47 plugins is the Notion trap all over again" — consistent, but the quote is attributed to no one in either article, while `karpathy-second-brain-system.md` (raw) contextualizes it as a general principle from the Karpathy/Spisak method. Minor attribution gap, not a contradiction.

## Broken Cross-Links
None. All `[[cross-links]]` resolve to existing wiki files:
- `[[personal-knowledge-base-systems]]` — exists
- `[[flat-file-architecture]]` — exists
- `[[claude-code-workflows]]` — exists
- `[[ai-powered-web-scraping]]` — exists
- `[[personal-knowledge-base-systems|personal knowledge base]]` (aliased link in `claude-code-workflows.md`) — resolves correctly

## Unsourced Claims

**`flat-file-architecture.md`**:
- The "Notion/Obsidian Trap" section quote ("Obsidian with 47 plugins is the Notion trap all over again") has no source citation — it appears in `karpathy-second-brain-system.md` but is unlinked
- The "When Flat Files Are Enough" and "When You Need More" lists are editorial synthesis with no source

**`claude-code-workflows.md`**:
- The entire article has no source references. The Claude Code plugin list (feature-dev, hookify, ralph-loop, skill-creator) is current knowledge with no backing raw file. The "Key Patterns" and "Prompt Patterns" sections are unsourced.

**`ai-powered-web-scraping.md`**:
- The "Knowledge Base Workflow" steps and "Use Cases" section have no source citations (claims are derivable from `agent-browser-vercel.md` but not explicitly linked)

**`personal-knowledge-base-systems.md`**:
- "Related in spirit to Vannevar Bush's Memex (1945)" — no source
- "The Anti-Pattern" section quote has no source citation (appears in `karpathy-second-brain-system.md`)
- Tooling subsection (Marp, Dataview, Obsidian graph view) — partially sourced via `karpathy-llm-wiki-gist.md` but the link is not explicit in those paragraphs

## Suggested New Articles

1. **aws-cloud-architecture** — Cloud Architecture is a listed interest with zero articles. Could cover serverless patterns, IAC approaches, common AWS service combinations. Relevant for both work KB and aligns with personal AWS cert study.
2. **customer-success-frameworks** — Customer Success is a listed interest with zero articles. Strategic account management, onboarding frameworks, health scoring, QBR structures.
3. **llm-prompting-strategies** — Complements existing AI articles; covers prompt patterns, chain-of-thought, few-shot, tool use, structured outputs. Would cross-link naturally with `personal-knowledge-base-systems.md` and `claude-code-workflows.md`.
4. **ecommerce-growth-operations** — Business & E-commerce is a listed interest with zero articles. Growth loops, conversion optimization, inventory and ops strategies.
5. **devops-and-ci-cd** — Software Engineering has only the flat-file-architecture article. A DevOps/CI-CD article would round out the category and provide practical workflow documentation.

## Stale Content
- `ai-powered-web-scraping.md` cites "26K+ GitHub stars" for agent-browser — point-in-time figure from April 4, 2026; will drift over time.
- `claude-code-workflows.md` lists Claude Code plugins (feature-dev, hookify, ralph-loop, skill-creator) — plugin ecosystems evolve; this list may become outdated.
- No deprecated tools or past dates found.

## Cross-Domain Issues
Clean. No personal content (family, health, finance, hobbies) found in work wiki. `personal-knowledge-base-systems.md` touches a topic relevant to both domains but is correctly housed in work (KB automation is a listed work interest), with no personal details included.

## Orphan Raw Files
None. All three raw files are referenced by wiki articles:
- `agent-browser-vercel.md` → referenced by `ai-powered-web-scraping.md`
- `karpathy-llm-wiki-gist.md` → referenced by `flat-file-architecture.md` and `personal-knowledge-base-systems.md`
- `karpathy-second-brain-system.md` → referenced by `flat-file-architecture.md` and `personal-knowledge-base-systems.md`

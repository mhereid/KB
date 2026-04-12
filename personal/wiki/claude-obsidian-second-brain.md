# Claude + Obsidian Second Brain

A practical guide to building an AI-maintained "second brain" by pairing Claude Code with an Obsidian vault. The setup, popularized by @defileo and based on Andrej Karpathy's LLM Wiki pattern, uses Claude Code to incrementally build and maintain a persistent wiki of interlinked markdown files — effectively a knowledge base that compounds over time without manual bookkeeping. The key insight: point Claude Code at your Obsidian vault folder, and your second brain builds itself in the background while Obsidian serves as the visual window into it. [source](../raw/claude-obsidian-second-brain-defileo.md)

## Setup

1. **Install Obsidian** — create a vault (folder) for your knowledge base
2. **Install Claude Code** — the terminal-based AI assistant
3. **Point Claude Code at your vault** — the vault is just a directory of markdown files
4. **Add a schema file** (CLAUDE.md) — defines the three-layer architecture: `raw/` (immutable sources), `wiki/` (AI-maintained articles), and a schema file that governs conventions and workflows

The schema file is the critical piece — it turns Claude from a generic chatbot into a disciplined wiki maintainer. You and the LLM co-evolve it over time as you figure out what works for your domain. [source](../raw/claude-obsidian-second-brain-defileo.md)

## Daily Operations

**Ingest** — Clip an article with Obsidian Web Clipper, it lands in raw/. Tell Claude to process it:

```
claude -p "I just added an article to /raw-sources. Read it, extract key ideas,
write a summary to /wiki/summaries/, update index.md, and update any existing
concept pages this connects to. Show me every file you touched."
```

One article can touch 10–15 wiki pages — surfaces unexpected connections, flags contradictions, logs every change. [source](../raw/claude-obsidian-second-brain-defileo.md)

**Query** — Ask Claude against the wiki. It scans the index, pulls relevant pages, answers with citations. Best outputs get saved back into the wiki so insights compound rather than vanishing into chat history.

**Lint** — Weekly health check: contradictions between pages, orphan pages, concepts mentioned without dedicated pages, outdated claims. Run one command, get a report with specific fixes. Maintenance stops being your job.

**Morning briefing** — Schedule a cron job that reads your Memory.md, checks for new raw sources in the last 24 hours, and prints a clean briefing to the terminal at 7:30 AM. Set once, runs forever.

**Transcript processing** — Feed call transcripts → extract decisions, action items with owners/deadlines, 3-bullet summary → auto-file to Action-Tracker.md, Decision-Log.md, and client notes. [source](../raw/claude-obsidian-second-brain-defileo.md)

## What Goes in the Vault

Everything you consumed in the last year that disappeared:

- Books you finished and forgot
- Podcasts that changed how you think
- Articles saved at 11pm and never reopened
- YouTube deep-dives that taught more than any course
- Kindle highlights never revisited
- Research before big decisions
- Old project notes
- Lessons from things that went wrong

No existing material? Talk to Claude for 20 minutes about your work, goals, what you're building. Save that as your Memory file — enough to make the first session feel like Claude actually knows you. The vault doesn't need to be complete to be useful. It just needs to be real. [source](../raw/claude-obsidian-second-brain-defileo.md)

## Why Most Second Brains Die — and Why This One Doesn't

Most second brain projects follow the same death cycle: start organized → maintenance piles up → skip it → system degrades → back to scattered notes → try to rebuild 6 months later → repeat.

Claude breaks that cycle because maintenance is just a command. Reorganizing your entire vault is a prompt. Migrating from Notion? One command processes every exported file, adds the right properties, and restructures everything. The tedious part of a knowledge base is the bookkeeping — cross-references, summaries, consistency across pages. LLMs don't get bored and can touch 15 files in one pass. [source](../raw/claude-obsidian-second-brain-defileo.md)

## Tooling Tips

- **Obsidian Web Clipper** — browser extension to convert web articles to markdown
- **Obsidian graph view** — visualize connections, hubs, and orphan pages
- **Download images locally** — Settings → Files and links → set attachment folder, bind "Download attachments" to a hotkey
- **Marp** — markdown slide deck plugin for generating presentations from wiki content
- **Dataview** — Obsidian plugin for queries over YAML frontmatter
- The vault is just a git repo — version history, branching, and collaboration for free

## Related Topics

- [[mission-psychological-services]] — an example of the pattern applied to personal finance tracking
- [[mentalyc-ai-note-companion]] — tool-driven leverage, a related concept

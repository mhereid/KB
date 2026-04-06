# How to Build Your Second Brain (Karpathy Method)

**Source**: Nick Spisak (@NickSpisak_) X post, April 4, 2026
**Original inspiration**: Andrej Karpathy's post on using AI to build personal knowledge bases

## Core Concept
Instead of keeping notes scattered across apps, dump everything into one folder. Then tell your AI to organize all of it into a personal wiki -- summaries, connections, articles -- that gets smarter every time you use it. No special software. No database. Just folders and text files.

## The System

### 1. Create Three Folders (2 Minutes)
```
my-knowledge-base/
  raw/          (source material - articles, notes, screenshots)
  wiki/         (AI-written organized version)
  outputs/      (answers, reports, research AI generates)
```
- raw/ is the junk drawer of source material
- wiki/ is where AI turns mess into organized content
- outputs/ is where answers to questions live

### 2. Fill Your Raw Folder (10 Minutes)
- Copy-paste articles into .md or .txt files
- Save screenshots or diagrams as images
- Export notes from whatever app you use
- Paste meeting notes, research papers, project docs
- Dump in bookmarks hoarded for months
- **Don't organize it. Don't rename anything. Don't clean it up. That's the AI's job.**

### 3. Automate Source Collection With Agent Browser (Optional)
Vercel Labs shipped agent-browser -- a free CLI tool that lets AI agents control a real browser (26K+ GitHub stars).
```
npm install -g agent-browser
agent-browser install
```
- Uses 82% fewer tokens than Playwright MCP
- AI can scrape 5-6x more pages within the same session
- Handles JavaScript-heavy sites, pages behind logins, interactive content

### 4. Write Your Schema File (5 Minutes)
Create a CLAUDE.md (or AGENTS.md or README.md) in the project root. This tells the AI:
- What the knowledge base is about
- How it's organized
- Rules for the wiki (one file per topic, summaries, linking, INDEX.md)
- Your interests/focus areas

Karpathy confirmed he keeps his schema "super simple and flat" in an AGENTS.md file.

### 5. Tell Your AI to Compile the Wiki (15 Minutes)
Prompt: "Read everything in raw/. Then compile a wiki in wiki/ following the rules in CLAUDE.md. Create an INDEX.md first, then create one .md file per major topic. Link related topics. Summarize every source."

**Important**: Don't edit the wiki by hand. That's the AI's job. You read it, ask questions against it, and the AI keeps it updated.

### 6. Ask Questions and Save Answers (Ongoing)
Example prompts:
- "Based on everything in wiki/, what are the three biggest gaps in my understanding of [topic]?"
- "Compare what source A says about [concept] vs what source B says. Where do they disagree?"
- "Write me a 500-word briefing on [topic] using only what's in this knowledge base."

Save answers to outputs/ or have AI update wiki articles with new insights. **Every question makes the next answer better. That's the loop.**

### 7. Run a Health Check (Monthly)
Prompt: "Review the entire wiki/ directory. Flag any contradictions between articles. Find topics mentioned but never explained. List any claims that aren't backed by a source in raw/. Suggest 3 new articles that would fill gaps."

Key insight from @HFloyd: "When outputs get filed back, errors compound too." Run periodic health checks to catch this.

### 8. Tool Choice Doesn't Matter
Karpathy: "I'm trying to keep it super simple and flat. It's just a nested directory of .md files."

- Could use Claude Code, VS Code, Obsidian, Notepad
- The AI doesn't care what app opens the files
- What matters is the folder structure and the schema
- "Obsidian with 47 plugins is the Notion trap all over again"
- Flat files and a good schema outperform fancy tool stacks 90% of the time

## Key Takeaways
1. Three folders + one schema file = the entire system
2. AI maintains the wiki, you maintain the raw sources
3. The compounding loop: questions -> answers -> saved back -> better future answers
4. Monthly health checks prevent error compounding
5. Simple and flat beats complex tooling

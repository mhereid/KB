# Agent Browser by Vercel Labs

**Source**: Referenced in Nick Spisak's X post, April 4, 2026

## Overview
A free CLI tool by Vercel Labs that lets AI agents control a real browser. 26K+ GitHub stars.

## Installation
```bash
npm install -g agent-browser
agent-browser install
```
The second command downloads a dedicated Chrome browser.

## Usage
```bash
agent-browser open https://some-article-you-want.com
agent-browser get text "article"
```

## Key Benefits
- 82% fewer tokens than Playwright MCP
- AI can scrape 5-6x more pages within the same session
- Handles JavaScript-heavy sites that load content dynamically
- Works with pages behind logins
- Handles research papers with interactive figures
- Manages scrolling, clicking "load more," navigating menus

## Use Case for Knowledge Bases
Workflow: find an article -> tell AI "scrape this URL and save it to raw/" -> agent-browser handles the rest. Raw folder fills itself automatically.

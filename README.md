# Personal Knowledge Base

An AI-maintained personal knowledge base using flat markdown files. Inspired by [Andrej Karpathy's approach](https://x.com/karpathy) to building a second brain with AI.

## Structure

```
kb/
  CLAUDE.md              Shared rules & cross-domain conventions
  personal/
    CLAUDE.md            Personal schema & interests
    raw/                 Source material
    wiki/                AI-organized articles
    outputs/             Generated reports & answers
  work/
    CLAUDE.md            Work schema & interests
    raw/                 Source material
    wiki/                AI-organized articles
    outputs/             Generated reports & answers
```

## Domains

**Personal** -- Fitness & health, family & parenting, sports & fantasy, personal development, personal finance

**Work** -- AI & LLMs, software engineering, business & e-commerce, cloud architecture, customer success

## How It Works

1. Drop source material into the appropriate `raw/` folder
2. AI compiles organized wiki articles in `wiki/`
3. Ask questions, save answers to `outputs/`
4. Run monthly health checks to catch errors
5. Cross-domain references link between personal and work when topics overlap

See each domain's `wiki/INDEX.md` for the full article index.

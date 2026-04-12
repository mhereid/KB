# Claude Managed Agents

Claude Managed Agents is Anthropic's pre-built, configurable agent harness that runs in managed infrastructure. You define an agent as a template — model, system prompt, tools, skills, MCP servers, files/repos — and the harness plus infrastructure are provided. The system is designed to keep pace with Claude's rapidly growing intelligence and support long-horizon tasks that can exceed 10 human-hours of work. Launched April 2026. [source](../raw/claude-managed-agents-launch-rlancemartin.md)

## Why It Exists

Two core challenges drove the design:

1. **Harnesses need to keep up with Claude.** Agent harnesses built on the messages API encode assumptions about what Claude can't do. Those assumptions grow stale as Claude gets more capable, bottlenecking performance. Harnesses need continual updates to keep pace.
2. **Claude is running for longer.** Claude's task horizon is growing exponentially (already exceeding 10 human-hours on METR). Long-horizon tasks need infrastructure that is safe, resilient to failures, and supports scaling to many agent teams.

The Claude Agent SDK was the first step (a general-purpose harness). Managed Agents is the next: a system with the harness *and* managed infrastructure for safe, reliable execution over the time horizons expected for future Claude. [source](../raw/claude-managed-agents-launch-rlancemartin.md)

## Key Concepts

- **Agent** — A versioned config housing the agent's identity: model, system prompt, tools, skills, MCP servers. Created once, referenced by ID.
- **Environment** — A template describing how to provision the sandbox (runtime type, networking policy, package config).
- **Session** — A stateful run using the agent config and environment. Provisions a fresh sandbox, mounts per-run resources (files, GitHub repos), stores auth in a secure vault.

One agent can have many sessions. Think: agent = configuration, environment = sandbox template, session = execution. [source](../raw/claude-managed-agents-launch-rlancemartin.md)

## Getting Started

```
$ claude update
$ claude
/claude-api managed-agents-onboarding
```

Also available: SDK quickstart (Python, TypeScript, Java, Go, Ruby, PHP), CLI subcommands for all API resources, and prototyping in Claude Console. [source](../raw/claude-managed-agents-launch-rlancemartin.md)

## Usage Patterns

| Pattern | Description | Example |
|---------|-------------|---------|
| **Event-triggered** | Service triggers agent automatically | Bug flagged → agent writes patch and opens PR |
| **Scheduled** | Agent runs on a cron | Daily briefs of X activity or team agent status |
| **Fire-and-forget** | Human triggers via Slack/Teams | Assign task → get back deliverables (spreadsheets, slides, apps) |
| **Long-horizon** | Extended autonomous runs | Research tasks, applying libraries to engineering blog content |

[source](../raw/claude-managed-agents-launch-rlancemartin.md)

## Architecture: Brain / Hands / Session

The engineering team decoupled three interfaces:

- **Brain** — Claude and its harness (expected to constantly evolve)
- **Hands** — Sandboxes and tools that perform actions
- **Session** — The log of session events

Each can fail or be replaced independently. This separation gives reliability, security, and flexibility to add future harnesses, sandboxes, or session infrastructure. The key insight: building agents to scale with Claude's intelligence is an **infrastructure challenge**, not strictly a harness design problem. [source](../raw/claude-managed-agents-launch-rlancemartin.md)

## SDK & CLI

- **SDKs** (6 languages) — code-facing, import to drive sessions at runtime
- **CLI** — terminal-facing, every API resource exposed as a subcommand
- **Common pattern** — CLI for setup, SDK for runtime. Store agent templates as YAML in git, apply via CLI in deploy pipeline. [source](../raw/claude-managed-agents-launch-rlancemartin.md)

## Related Topics

- [[claude-code-workflows]]
- [[agent-harness-hill-climbing]]

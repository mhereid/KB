# Agent Harness Hill-Climbing with Evals

Better-Harness is LangChain's prototype system for autonomously improving agent harnesses using evals as a learning signal. The core analogy: evals are to agent harnesses what training data is to ML models. Just as gradient descent optimizes model weights using training examples, eval-driven harness engineering optimizes prompts, tool descriptions, and agent scaffolding using eval results as the gradient signal. The system emphasizes generalization over overfitting, with holdout sets, human review gates, and trace-level diagnosis. [source](../raw/better-harness-hill-climbing-evals-vtrivedy10.md)

## Core Analogy

```
model + training data + gradient descent → better model
harness + evals + harness engineering   → better agent
```

Evals encode desired production behavior. Each eval contributes a signal — "did the agent take the right action?" — that guides the next proposed edit to the harness. The same rigor applied to ML training data quality should go into eval design. [source](../raw/better-harness-hill-climbing-evals-vtrivedy10.md)

## Sourcing Good Evals

| Source | Characteristics |
|--------|----------------|
| **Hand-curated** | High value, hard to scale. Team writes examples capturing desired production behavior. |
| **Production traces** | High throughput. Every agent interaction generates a trace; failures become eval cases. Dogfooding + Slack feedback builds shared knowledge. |
| **External datasets** | Useful but require manual curation to match desired behaviors. |

**Tag everything** — every eval gets behavioral category tags (tool selection, multi-step reasoning, etc.). Tags enable meaningful holdout sets and targeted experiments, and save money by running eval subsets. [source](../raw/better-harness-hill-climbing-evals-vtrivedy10.md)

## The Hill-Climbing Recipe

1. **Source and tag evals** — hand-write, mine from traces, adapt external datasets. Regularly prune saturated evals.
2. **Split per category** — create Optimization and Holdout sets. Critical for avoiding overfitting.
3. **Run baseline** — ground all updates against initial performance on both sets.
4. **Optimize** — each iteration: diagnose errors from traces → propose one targeted harness change → validate. Scope to one change at a time to avoid confounding.
5. **Validate** — check that proposed change passes new evals without regressing existing passing cases. Agent gets context of regressions to fix in next iteration.
6. **Human review** — manually review changes and edge cases metrics miss. Catches overfit instructions that waste tokens even if they don't hurt generalization.

[source](../raw/better-harness-hill-climbing-evals-vtrivedy10.md)

## Types of Harness Changes Discovered

- **Prompt/instruction updates** (most common) — targeted fixes like "when querying multiple files with dependent information, offload to filesystem and re-aggregate before final answer"
- **Tool description updates** — better descriptions of how to use and compose tools, especially when new tools are injected into the harness
- **Tool suite disambiguation** — editing the overall tool suite to disambiguate similar tools

[source](../raw/better-harness-hill-climbing-evals-vtrivedy10.md)

## Generalization vs. Overfitting

**The obvious problem**: limited data.
**Fix**: Quality > quantity — small set of well-tagged evals covering key behaviors beats thousands of noisy ones.

**The subtle problem**: agents are famous cheaters — the loop wants to "make number go up" and doesn't know about generalization.
**Fix**: Holdout sets as proxy for true generalization + human review as second signal = semi-automated improvement that avoids unwanted production behaviors.

Results on Claude Sonnet 4.6 and Z.ai GLM-5: nearly full generalization to holdout sets with totally unseen examples. [source](../raw/better-harness-hill-climbing-evals-vtrivedy10.md)

## Evals as Regression Tests

Once an agent handles a case correctly, the eval becomes a regression test (similar to TDD). Select a subset of "always-pass" evals and flag suspiciously when they fail. Spring cleaning is important — regularly assess whether evals are still useful given more intelligent models or different desired behaviors. [source](../raw/better-harness-hill-climbing-evals-vtrivedy10.md)

## The Trace Flywheel

```
more usage → more traces → more evals → better harness
```

Traces enable:
- **Automated error detection** — classify and cluster failures in production
- **Eval generation from production** — mistakes and user corrections become eval cases
- **Harness version comparison** — side-by-side trace diffs show what changed

All runs logged to LangSmith for trace-level diagnosis, production monitoring, and eval mining. [source](../raw/better-harness-hill-climbing-evals-vtrivedy10.md)

## Related Work

- **Meta-Harness** (Stanford) — formalizes steps to optimize harnesses
- **Auto-Harness** (DeepMind) — automated harness optimization
- **Harness Improvement Loop** (LangChain prior work) — hill-climbing Terminal Bench 2.0 by tweaking the harness layer

## Related Topics

- [[claude-managed-agents]]
- [[claude-code-workflows]]

---
name: token-optimizer
description: "This skill should be used when the user or agent wants to reduce token usage, keep long conversations within context limits, or prefer concise responses without losing effectiveness. Guides budget-aware planning, proactive compacting, checkpoints, and relevance-based context pruning."
category: efficiency
risk: safe
source: community
tags: "[tokens, context, efficiency, optimization, compacting, pruning]"
date_added: "2026-03-10"
---

# token-optimizer

## Purpose

To guide the agent toward efficient token usage while preserving effectiveness. The agent applies compact responses, budget-aware planning, optional checkpoints, and relevance-based context handling so that fewer tokens are consumed without sacrificing task completion or clarity.

## When to Use This Skill

This skill should be used when:
- The user explicitly asks to save tokens, reduce context usage, or get shorter responses
- The user requests a plan with a token or context budget in mind
- A long or multi-step task would benefit from planning with limited context
- The conversation is growing long and could benefit from summarization or context pruning
- The user asks to compact context, summarize before continuing, or create a checkpoint

## Core Rules

1. **Budget-aware plans.** For long or multi-step tasks, propose a brief step-by-step plan before executing. State what will be done at each step in one or two sentences. Avoid dumping full detail in a single reply; spread detail across steps and reference files by path when possible.

2. **Proactive compacting.** When context is filling or the user asks to compact: offer to summarize older messages or less relevant context before continuing. Never remove or summarize the system prompt or recent error messages. Preserve the last few exchanges and any user-stated constraints.

3. **Checkpoints.** In multi-step tasks, suggest checkpoints: a short summary of what is done, what is next, and the current state. This lets the user (or the agent after a reset) continue without re-sending the full history. See `references/checkpoint-format.md` for a template.

4. **Tiered detail.** Load or cite only the level of detail needed for the current step. Prefer linking to `references/` or file paths instead of pasting long blocks into the main reply. Expand only when the user asks or when the next step requires it.

5. **Relevance-based pruning.** When summarizing or compacting context: keep errors, recent decisions, and the current task state; trim repetition, long logs, and obsolete context. Do not prune more than roughly 40% of the conversation without the user confirming, and always keep the most recent N messages (e.g. 5–10) intact when possible.

6. **Concise responses.** Prefer short, direct answers. Use lists and tables when they clarify. Avoid repeating the user’s prompt verbatim. Answer in the user’s preferred language without adding extra filler.

7. **Code and files.** Include only the code snippets that are relevant to the change or question. Reference files by path instead of pasting entire files unless strictly necessary for the current step.

## Extended Guidance

- **Token estimation:** For planning with a rough token budget, use the heuristics in `references/token-estimation.md`.
- **Pruning strategies:** For more detail on what to keep vs. summarize when compacting, see `references/pruning-strategies.md`.
- **Checkpoint format:** For a standard checkpoint template, see `references/checkpoint-format.md`.

Apply these rules whenever this skill is active or when the user asks to optimize token usage. Efficiency must not reduce the quality or correctness of the agent’s output.

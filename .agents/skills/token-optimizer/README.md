# token-optimizer

Agent-agnostic skill to reduce and optimize token usage without sacrificing effectiveness. The agent applies concise responses, budget-aware planning, optional checkpoints, and relevance-based context handling.

## When to Use

Use this skill when you or the agent want to:

- Save tokens or reduce context usage
- Get shorter, more focused responses
- Plan long tasks with a token or context budget
- Compact or summarize context before continuing
- Create checkpoints so work is preserved across resets or compact actions

Trigger phrases include: "optimize tokens", "save tokens", "reduce context usage", "shorter responses", "plan with token limit", "compact context", "summarize before continuing".

## How It Works

The agent follows the rules in `SKILL.md` when this skill is active or when you ask to optimize tokens. No platform-specific setup or scripts are required. The skill lives under `.agents/skills/token-optimizer/` and can be used by any agent that loads skills from that directory (e.g. Cursor).

## Contents

- **SKILL.md** — Main instructions: when to use, core rules, and links to detailed guides.
- **references/** — Optional deeper guidance:
  - `token-estimation.md` — Rough token counts and budget planning.
  - `pruning-strategies.md` — What to keep vs. summarize when compacting.
  - `checkpoint-format.md` — Template for checkpoints.

## License

Same as the parent repository.

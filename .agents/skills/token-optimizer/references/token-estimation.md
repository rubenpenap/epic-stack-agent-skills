# Token Estimation

Rough heuristics for planning with a token budget. Use these when the user asks for a budget-aware plan or when deciding how much context to include.

## Approximate Tokens by Content Type

- **Plain English (or similar):** ~4 characters per token, or ~250 words per 1k tokens.
- **Code:** ~3–4 characters per token depending on language and symbols; dense code (e.g. minified) can be closer to ~2 characters per token.
- **Markdown:** Similar to plain text; headers and list syntax add a small overhead.
- **Mixed conversation:** Assume ~3–4 characters per token for a typical turn (message + reply).

## Planning With a Budget

1. **Estimate current usage.** If the agent has access to message or character counts, approximate tokens as above. Otherwise, use message count: e.g. assume 200–500 tokens per short exchange, 500–1500 per long exchange.
2. **Reserve headroom.** Leave 10–20% of the stated or implied context limit for the next few turns and for the agent’s reply.
3. **Prioritize.** Allocate the remaining budget to: (a) system/instructions, (b) latest user goal and errors, (c) recent decisions and state, (d) older context only if needed. Summarize or drop the rest.
4. **Checkpoints.** If the task is long, plan checkpoint points (e.g. after each major step) so the user can trim history and continue with a short summary instead of full context.

These are guidelines only; actual tokenization depends on the model and tokenizer. When in doubt, prefer slightly more conservative estimates so the conversation stays within limits.

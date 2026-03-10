# Pruning Strategies

Guidance on what to keep and what to summarize or omit when compacting context, so that token use drops without losing effectiveness.

## Always Keep

- **System prompt and instructions.** Do not summarize or remove; the agent needs them for behavior and constraints.
- **Recent errors and stack traces.** Keep the last error (and optionally one or two before) in full so debugging can continue.
- **User’s current goal and constraints.** The latest stated objective, preferences, and “do not” rules.
- **Last N full turns.** Keep the most recent 5–10 message pairs intact so the immediate dialogue remains clear.

## Prefer to Summarize

- **Older successful steps.** Replace with one or two sentences: “Step 1–3 done: implemented X, Y, Z; no errors.”
- **Long code blocks that are no longer in focus.** Keep file paths and a one-line description; drop the full body unless the next step needs it.
- **Repeated explanations.** Keep one clear version; drop duplicates.
- **Long logs or trace output.** Replace with a short summary (e.g. “Build succeeded; tests passed; 3 warnings in file X”).

## Prefer to Omit

- **Duplicate or near-duplicate messages.** Keep a single representative instance.
- **Context that is obsolete.** Old branches of the conversation that are no longer relevant to the current goal.
- **Purely social or off-topic turns.** Unless the user explicitly asks to preserve them.

## Limits

- Do not prune more than about 40% of the visible context in one go without the user confirming.
- After pruning, state briefly what was summarized (e.g. “Summarized steps 1–4 and older code; kept last 8 messages and current error.”) so the user knows what remains.

Apply these strategies when the user asks to compact or when the agent suggests summarizing to stay within context limits.

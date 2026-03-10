# Checkpoint Format

A short template the agent can use when suggesting or creating a checkpoint so the user (or the agent after a reset) can continue without full history.

## Template

```
**Checkpoint**
- **Done:** [1–3 sentences: what was completed and key outcomes]
- **Next:** [1–2 sentences: immediate next step or goal]
- **Context:** [Optional: important paths, decisions, or constraints to remember]
```

## Example

```
**Checkpoint**
- **Done:** Added JWT middleware in `app/auth.ts`; login returns a token; `/api/protected` checks the header.
- **Next:** Write tests for the protected route and invalid-token cases.
- **Context:** Using `Authorization: Bearer <token>`; secret in env `JWT_SECRET`.
```

## When to Suggest a Checkpoint

- After finishing a logical step in a multi-step task.
- Before the user might run a “compact” or “clear” action.
- When the conversation is long and the next phase could start from a clean context with this summary.

Keep checkpoints to a few lines so they add minimal tokens while preserving continuity.

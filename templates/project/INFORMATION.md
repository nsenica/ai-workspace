# Project name — information ownership

**Optional project-local routing.** Fill in only the categories you use. This file documents where project knowledge is **canonically recorded**; it does not grant permission to write there. Use real, safe links or paths. If the project has no external system, AI Workspace can own the relevant categories.

| Category | Canonical destination | Notes / permission gate |
| --- | --- | --- |
| Ideas | <Backlog.md, issue tracker, or `IDEAS.md`> | <Who may register or triage?> |
| Decisions | <Backlog.md, ADRs, or `DECISIONS.md`> | <Who approves decisions?> |
| Tasks / acceptance | <tracker, or project-selected local record> | <Who creates/changes statuses?> |
| Research / knowledge | <project docs or `knowledge/`> | <Authoritative versus exploratory?> |
| Test/review evidence | <controlled evidence store or `evidence/`> | <Provenance and access restrictions?> |
| Live/runtime state | <operational system or not applicable> | <Never infer from handoff> |

**Always local to AI Workspace unless explicitly replaced:** `HANDOFF.md` (current coordination) and, when needed, `PENDING.md` or `pending/` (unmaterialized conversation context). Neither is a substitute for canonical records.

## Working rules

- Only preserve **valuable unresolved** discussions in pending context.
- Before creating or editing a durable record, search the declared destination and respect its approval gates.
- On successful materialization, verify the authoritative record by read-back and remove the redundant pending content.
- If materialization cannot be verified or is partial, preserve the unresolved context and disclose the gap.
- When ownership is unknown, **do not assume** that a local note is an approved task or decision.

See [context lifecycle](../../docs/CONTEXT_LIFECYCLE.md) for details.

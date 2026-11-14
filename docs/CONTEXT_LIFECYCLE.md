# Conversational context: capture, route, materialize, retire

Conversations often produce useful information **before anyone is ready to commit it to a project's durable system**. AI Workspace bridges that gap. It must **not** become a competing backlog or a collection of duplicate, stale decisions.

## Three kinds of records

1. **Working context (provisional):** An unfinished discussion, emerging idea, option, unresolved question, or agreed postponement that would be costly to reconstruct. Preserve in `PENDING.md` or `pending/<topic>.md` until resolved.
2. **Durable project information:** An idea, decision, research finding, or other record in the **canonical location for that category**. That may be Backlog.md, GitHub Issues, a project's own files, a database, or AI Workspace itself.
3. **Current handoff:** A compact pointer to relevant pending topics, verified state, and the next action. It is not a second copy of either record.

The **owner of information is configured per project and category**, not fixed by this template. See [INFORMATION.md template](../templates/project/INFORMATION.md). Explicit project rules and real system permissions override suggested defaults.

## Choose where information belongs

| Situation | Recommended handling |
| --- | --- |
| Project has Backlog.md or another designated store for ideas/decisions | Materialize there **only with authorization**. AI Workspace holds only unfinished/unmaterialized context, plus links needed for a current handoff. |
| Project has a tracker for tasks but not ideas | Route tasks to the tracker; explicitly choose AI Workspace or another store for ideas. |
| Project has no suitable durable store | AI Workspace **may be the canonical store** for its own ideas, decisions and knowledge (for example `IDEAS.md` and `DECISIONS.md`). |
| Ownership is unknown or conflicting | Preserve as pending if valuable and permitted; identify the ambiguity. Do **not** invent a canonical task, decision, or approval. |
| Discussion is casual, redundant or already captured | Do not create another record. |

**Authority is not permission.** Declaring Backlog.md as the ideas destination does not authorize an agent to create a backlog idea, accept a decision, change a task, or publish anything. Declaring AI Workspace canonical for ideas does not authorize the agent to approve ideas or implement them.

## Capture when there is something worth resuming

Create/update provisional context when a meaningful conversation is **paused, deferred, handed to a different agent, or at risk of being lost**, and it has not yet been durably recorded elsewhere. Examples:

- We explored a feature, but agreed to finish another milestone before deciding whether to register it.
- We narrowed several technical options, but need more evidence.
- The user explicitly deferred a decision, and the reason matters.
- A useful research observation surfaced without a suitable canonical home yet.

An agent with standing **workspace-write permission** can preserve useful provisional information without asking to save each note. If read-only or lacking access, propose the note without claiming it was stored.

Capture a **short synthesis**, not a transcript: context and motivation, useful findings, open questions, explicitly rejected options, what is *not* approved, revisit trigger, intended destination, and provenance of the discussion. A tentative suggestion is not an accepted decision.

A conversation can continue without any commit. Update when its **meaningful state changes**, at a natural pause, before a substantial handoff, or when authoritative materialization is verified. No timer, per-message write, or automatic stale-item purge is required. A topic merely being old is **not** grounds for discarding it.

## Lifecycle

```text
Conversation
    │ meaningful, not yet canonical
    ▼
Pending working context ────► Resume / revise / pause
    │
    ├──► Authorized materialization ─► Read back & verify ─► Retire pending
    │             │
    │             └── write failed / uncertain / partial ──► Keep pending
    │
    └──► Explicitly discarded ────────────────────────────► Retire pending
```

A recorded **deferral** in the canonical system is already materialized; do not also keep an active pending copy just because work is postponed. A conversation deferred **before** materialization belongs in pending context.

## Materialize safely

1. **Find the destination.** Read the project's information-ownership mapping and relevant canonical record(s); search for an existing matching idea/decision/task before creating one.
2. **Check authority.** Determine whether the current task actually authorizes that write or status transition. If not, keep the context pending and present a proposal.
3. **Write intentionally.** Carry over material rationale and constraints, distinguishing open questions from approved scope. Never invent acceptance or provenance.
4. **Read back.** Verify the authoritative record identifier, contents, status, and publication as far as accessible. An agent-reported successful write or unverified local draft alone is insufficient.
5. **Retire only what has a home.** Remove the resolved material from active `PENDING.md` / `pending/` once it is verified. If some questions remain unmaterialized, retain **only that unresolved remainder**.
6. **Keep a pointer only if useful.** The current `HANDOFF.md` may link to the canonical record when the next step depends on it. Do not maintain a parallel synopsis that can drift.

If a write times out or the response is lost, **reconcile by searching/reading the destination before retrying**; blindly creating again risks duplicates. If the read-back cannot be performed, say *materialization unverified* and leave pending intact.

After an authorized explicit discard, retire provisional context; optionally persist the **reason** as a durable decision **only** if the project wants to remember it. A rejected idea already recorded canonically should not become a duplicate local rejection record.

Retiring means **removing from active context**, not erasing Git history, backups, or copies. This method is not a secure deletion process; do not place secrets into pending files in the first place.

## Keep project handoffs small

The handoff should mention a pending discussion only when it affects the present next step or avoids a likely context loss. It can link to `PENDING.md` or a topic file; it should not reproduce the debate. When context is materialized, update that pointer if necessary, rather than copying the new record.

## Cases to test

- **External backlog:** The team pauses an unregistered discussion. It survives a fresh agent session. No backlog item is created until authorized. Once a matching backlog item is verified, the pending entry is removed.
- **No external system:** The same discussion is captured as pending; when approved for durable recording, it moves to the project's local `IDEAS.md` or `DECISIONS.md`, with no duplicate pending text.
- **Failure:** An external write appears successful but cannot be read back. Keep the provisional content and mark verification uncertain.
- **Already exists:** The destination already holds the idea. Link/reconcile rather than create a duplicate.
- **Discard:** A user explicitly drops the exploration. Clear the pending entry without inventing a task or approval.

See the [fictional examples](../examples/sample-project/README.md) and [getting started](GETTING_STARTED.md).

# Method: continuity with bounded authority

The method is intentionally independent of any AI vendor, agent orchestration system, or task tracker.

## The cycle

**Resume:** Read the project's short current handoff, information-ownership map and relevant pending context, plus authoritative decisions/evidence as needed. Start in the assigned namespace.

**Verify:** Compare mutable claims with authorized source systems. Distinguish live state from historical snapshots and independently checked facts from unverified reports.

**Work:** Act only within the current assignment. Writing context is not permission to edit source, task status, policies, budgets or deployments.

**Preserve:** Capture valuable **unmaterialized** conversational context when paused, and store other useful artifacts in permitted locations. Route durable ideas and decisions to each project's designated system; avoid duplication and context dumping.

**Publish:** Inspect precisely what will be committed, check confidentiality, preserve attribution, push to the intended private remote and verify the actual remote revision.

**Hand off:** Keep the active handoff's top section current, with the next actor/action and hard stop conditions. After verified materialization, retire redundant provisional notes.

## What belongs where?

| Question | Prefer |
| --- | --- |
| What should the next agent do? | `HANDOFF.md` |
| Who owns ideas and decisions? | Project `INFORMATION.md` (if used); authoritative system wins |
| What unfinished discussion must survive? | `PENDING.md` / `pending/<topic>.md` |
| Why did we choose this approach? | Project's canonical decisions store; `DECISIONS.md` if local |
| What exactly did a test/review show? | Canonical evidence location, often `evidence/<subject>/` |
| Where are the many supporting files? | `INDEX.md` |
| What is the actual current task status? | Project's designated task authority (tracker or explicitly selected local store) |
| What code is shipping? | Source repository and deployment |
| What is live now? | Runtime/operational system |

## Discussion capture and retirement

Capture when a meaningful conversation is paused, deferred or handed over **before** it has a canonical record. Keep the motivation, conclusions, open questions, non-approvals, revisit trigger and intended destination—not the whole transcript. No compulsory daily/weekly updates; changes are event-driven.

A formally recorded **deferred** idea is already materialized; a deferred **conversation** may still be pending. Before registering a record, search for duplicates and check write authorization. Verify the destination **by read-back** before deleting pending material; on uncertainty keep the unresolved portion. Retire explicitly discarded discussions only on an authorized disposition. [Full lifecycle](CONTEXT_LIFECYCLE.md).

## Handoff freshness

The handoff is a **navigation aid**, not a universal source of truth. It may be stale the moment it is committed.

Write a `Last checked` timestamp, identify the last **verified** revision and name the remaining unknowns. If a new session cannot confirm current state, its output should say that explicitly.

## How much should be preserved?

Preserve what would materially help an authorized new contributor make the next correct decision, reproduce a meaningful result or avoid repeating an investigation.

Avoid a hard maximum file size, but be suspicious when an active handoff grows by appended daily reports. Move historical detail to a dedicated evidence or archive record and keep a pointer from the current summary. A topic removed from active pending context may still exist in Git history; this is not secure deletion.

## Two-agent acceptance exercise

A useful test is to ask a **fresh, read-only agent** to infer the correct next gate using only the workspace and allowed authoritative reads.

Success is not mere fluency. The agent should:
- identify the current task and precise authoritative sources;
- separate reported claims from reproduced evidence;
- avoid claiming it inspected inaccessible resources;
- identify the next step **and required authorization**;
- avoid expanding into other projects.

If that fails, improve the handoff or guidance before adding automation.

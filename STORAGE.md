# Storage and evidence conventions

These are flexible conventions, **not a fixed file-type allowlist**. Preserve what lets the next contributor discover, understand, reproduce, verify or reuse meaningful work.

## Per-project layout

Create `projects/<slug>/HANDOFF.md`. Add other files only when useful:

| Path | Purpose |
| --- | --- |
| `HANDOFF.md` | **Current** state, last check, authorities, next gate and boundaries |
| `INFORMATION.md` | Optional **per-category** map of canonical stores and approval gates |
| `PENDING.md` or `pending/` | Useful **unmaterialized** discussions; never a shadow task backlog |
| `IDEAS.md` / `DECISIONS.md` | Local canonical registers **only for categories assigned to AI Workspace** |
| `INDEX.md` | Optional navigation when material grows |
| `knowledge/` | Research, observations, useful context |
| `designs/` | Diagrams, prototypes, design work |
| `evidence/<subject>/` | Reviews, logs, reports, comparisons, reproducible checks |
| `artifacts/` | Other useful deliverables and generated outputs |
| `archive/` | Deliberately preserved historical snapshots |

Names under the project folder are examples, not required infrastructure. A project using Backlog.md, GitHub Issues, ADRs or other durable systems should **refer to those canonical records**, not mirror them. When a project has no suitable external storage, its own AI Workspace files may be designated canonical for ideas, decisions and other knowledge. [Lifecycle and materialization rules](docs/CONTEXT_LIFECYCLE.md).

## Keep active context useful

A handoff should lead with **current status, next actor/action, authoritative references, known uncertainty, and no-go boundaries**. Keep detailed discussions in provisional `PENDING.md` when not yet recorded canonically, and link to them only when relevant. Prefer updating the current summary and linking to evidence over endlessly appending chronologies. Git records changes; old accepted evidence should remain attributable and intact.

For a meaningful decision, preserve **decision, date, status, rationale, alternatives, implications, supersedes** (when relevant) **in the project's designated store**. Proposals should not masquerade as approvals. Merely pausing a discussion is not materialization; once a canonical record is verified, remove its redundant temporary copy from active pending context. Retiring a note does not securely erase Git history.

## Evidence provenance

For consequential evidence, provide the relevant fields:

- **Identity:** what task/check was evaluated, exact baseline and candidate revision (or declared uncommitted worktree fingerprint).
- **Origin:** when, by whom/what, with which commands, tool versions and environment.
- **Outcome:** passes, failures, skips, warning and uncertainty, not just a green/red label.
- **Verification:** producer-reported or independently reproduced? Who checked what?
- **Integrity:** size and SHA-256 of the **actual stored bytes** where valuable; redacted content has a new identity.
- **Limits:** missing material, selective checks, unverifiable external assertions, or access restrictions.

An **optional illustrative** machine-readable manifest is in [templates/evidence/manifest.example.json](templates/evidence/manifest.example.json). It is not currently enforced by a schema validator. Do not store a self-referential hash for the manifest itself.

## Data selection

Useful: unfinished discussions worth resuming, handoffs, plans, reproducible fixtures, exact failure-node lists, reviewed logs, comparisons, notes, mockups, research and verified references. **Don't create a second active idea or decision record** when a canonical one already exists.

Usually disposable: caches, routine transient outputs, complete copied source trees, duplicate reports and unreviewed giant dumps. Size alone is not a reason to delete accepted evidence, and raw formats are not prohibited merely because they are raw.

For large or restricted items, keep a durable access-controlled original elsewhere and record a safe pointer, owner/retention expectation, size/hash when verifiable, and access limitations. **Do not publish private evidence to a public artifact service**.

## Concurrent publication

Check the latest remote state; stage narrowly, review the diff, commit clearly and re-fetch to confirm publication. Use a branch or review gate for disputed, security-sensitive, or consequential changes. Never silently rewrite previously reviewed evidence.

Follow [security guidance](docs/SECURITY.md) before sharing material.

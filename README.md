# AI Workspace

**Persistent project context for humans and AI agents, backed by Git.**

AI conversations end. Project knowledge, decisions, and evidence should survive them.

AI Workspace is a small, tool-agnostic repository structure and operating method. It helps a new conversation, agent, model, or machine resume project work from preserved context **without treating a handoff as unquestionable truth**.

There is no server, database, orchestration engine, or mandatory model. Start with Markdown and Git.

## Quick start

1. Create a **private** repository from this template (or clone it and push to your own private remote). Do not use your work-in-progress repository as a public contribution branch.
2. Create `projects/<slug>/` from [templates/project/](templates/project/). Fill in `HANDOFF.md`; if the project has existing idea/decision/task systems, map them with the optional `INFORMATION.md` template.
3. Add the project to your private `WORKSPACE.md` using [WORKSPACE.example.md](WORKSPACE.example.md) as a starting point.
4. Give your agent access to the workspace **within an explicit approved scope** and ask it to read [AGENTS.md](AGENTS.md), `WORKSPACE.md`, and the relevant project handoff before working.
5. When a meaningful discussion pauses **before being recorded elsewhere**, preserve it as pending context if authorized. After milestones, refresh the handoff and evidence as needed; commit and verify publication.

Full first-run instructions: [Getting started](docs/GETTING_STARTED.md).

## The model

| Place | What it owns |
| --- | --- |
| Source repository | Code and source revision |
| Task/issue tracker (if used) | Tasks, acceptance, priorities and statuses assigned to it |
| Project's designated information stores | Canonical ideas, decisions, research and other records, category by category |
| Runtime/service | Actual operational state |
| **AI Workspace** | Handoffs and unmaterialized context; also canonical information **only for categories explicitly assigned to it** |
| Human or delegated authority | Permissions, approvals and exceptions |

Projects choose where each kind of information belongs. AI Workspace can itself hold canonical ideas or decisions **when so designated**, but must not duplicate a project's existing backlog. Recording context never authorizes changing tasks, approvals or deployments. A saved claim about a test or deployment is not proof it succeeded. [Context lifecycle](docs/CONTEXT_LIFECYCLE.md).

## Working rhythm

**Resume → Verify → Work within scope → Preserve → Publish and verify → Hand off.**

An active handoff answers: *Where are we? What's known? What remains uncertain? Who acts next? What must not happen without approval?* Unfinished discussions can remain in `PENDING.md` until materialized or deliberately discarded; the handoff links only to what matters next. [Method](docs/METHOD.md).

## What's in this repository?

- [AGENTS.md](AGENTS.md) — reusable instructions for contributing agents.
- [STORAGE.md](STORAGE.md) — practical retention, provenance, and evidence conventions.
- [Templates](templates/project/) — handoff, optional information ownership and pending discussion records, and local durable idea/decision registers.
- [Example](examples/sample-project/README.md) — a fictional two-agent continuation, including an explicitly illustrative evidence record.
- [Context lifecycle](docs/CONTEXT_LIFECYCLE.md) — capture unfinished discussions, route to a canonical store, verify, and retire redundant pending context.
- [Security](docs/SECURITY.md) — privacy, trust boundaries, credentials, and safe publication.
- [Upstream synchronization](docs/UPSTREAM_SYNC.md) — how to adopt public improvements in an existing private workspace.
- [WORKSPACE.example.md](WORKSPACE.example.md) — a personal project index and local settings example (copy to `WORKSPACE.md`).

Project-specific folders under `projects/` are your workspace, **not content to contribute upstream**. Private `WORKSPACE.md` is intentionally ignored by Git in this public foundation's default `.gitignore` so an initial clone does not accidentally stage it; a private downstream repository can explicitly `git add -f WORKSPACE.md` once reviewed.

## Principles

1. **Continuity over chat history.** Store the current gate and durable pointers, not entire conversations by default.
2. **Authority stays at the source.** Context is never a backdoor permission to change code, tasks, or deployments.
3. **Provenance over confidence.** Separate agent reports, independent verification, and unknowns.
4. **Capture unresolved value, within permission.** Remember conversations worth resuming, then retire temporary notes once their canonical record is verified.
5. **Small active state, rich supporting evidence.** Keep handoffs navigable while preserving material that helps reproduce or audit results.
6. **Public foundation, private by default in practice.** Share generic improvements; never automatically publish downstream project data.
7. **No mandatory stack.** Plain files and Git first; optional tooling only when it solves a demonstrated problem.

## Who is this for?

People collaborating with AI on long-running software or research projects, especially across multiple conversations, agents, or machines. The method works with manual prompting and can be adopted by automated systems later; it does **not** provide autonomy, isolation, or security controls by itself.

## Status

**Foundation v0 — private design/review stage.** Templates and the example are intentionally small. Public-release decisions (including the final license, contribution policy, and security review) are not complete. See [Release checklist](docs/RELEASE_CHECKLIST.md). No license grant is implied until a license is selected.

The fictional example contains no real project data. Always review the full tree and Git history before making any derivative repository public.

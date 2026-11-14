# Getting started

This quick start assumes you know basic Git commands. AI Workspace is a **method and file structure**, not software you install.

## 1. Create your own private workspace

From the GitHub template UI, choose **Use this template → Create a new repository** if the repository is configured as a template. Otherwise clone the repository and push it to a new, **private** remote you control.

Do not begin by making your project-context repository public. Review remote URL, visibility and collaborators before uploading anything.

## 2. Add one project

Create a folder `projects/<slug>/` (lowercase, simple name). Copy `templates/project/HANDOFF.md` to the new folder and fill it in.

Choose **where each category of durable information belongs**. If the project already uses Backlog.md, GitHub Issues, ADRs or another system, copy `templates/project/INFORMATION.md` into your project and fill in the routing rather than duplicating records. If no other store exists, you can use local `templates/project/IDEAS.md` and `DECISIONS.md` as canonical registers. `INDEX.md` remains optional. Copy templates into the project folder and delete placeholder rows before use.

Copy `WORKSPACE.example.md` to `WORKSPACE.md` and register your project. The upstream template ignores this local file to reduce accidental publication. To commit it to **your private repository only**, first inspect its content and remotes, then use `git add -f WORKSPACE.md`.

No commands here create or grant agent access. Configure your own tools separately.

## 3. Give the agent an explicit starting instruction

Use a prompt like:

> You are working on project `<slug>`. Your current assignment is to **read and summarize the next safe action only; do not write or execute changes**. Read `AGENTS.md`, `STORAGE.md`, `WORKSPACE.md` (if present), and `projects/<slug>/HANDOFF.md`. Identify the authoritative source systems, what is verified versus reported, blockers, and the next approval gate. If you cannot access a source, mark it unverified. Do not browse other project directories.

For an actual implementation task, separately state the exact read/write scope, source repositories, constraints and required approval/review gates. Do not assume a generic instruction grants access.

## 4. Capture a paused discussion (optional)

Suppose you discuss a future feature but decide to finish the current milestone **before recording it as a formal idea**. If permitted to write project context, create a short entry from `templates/project/PENDING.md` describing the motivation, useful findings, open questions, revisit trigger, and intended destination. This is **not** a Backlog task or approved decision.

When the discussion is later materialized, verify the external/local canonical record by **reading it back** before retiring the pending entry. If the write is blocked, partial or unverified, preserve the unresolved portion. If the discussion is explicitly discarded, retire it without inventing a task. See [context lifecycle](CONTEXT_LIFECYCLE.md).

## 5. Run one handoff cycle

1. Start a small task with a known authoritative issue/source revision (or clearly identified locally managed scope).
2. Have the contributor verify current state and work within authorization.
3. Save the minimal new context: current handoff, *a pointer to* canonical decisions or evidence if elsewhere, and permitted local records if designated. Do not mirror an external backlog.
4. Have the contributor review the diff for secrets, scope and truthfulness; commit to the **private** remote.
5. Open a fresh agent session, give only the project name and read-only resume prompt, then ask it to identify the next gate.
6. Compare that answer against the authoritative systems and amend unclear instructions.

For a completely fictional illustration, see [the example](../examples/sample-project/README.md).

## 6. Avoid these beginner traps

- Writing full conversation histories into every handoff.
- Calling an agent-reported test result independently verified.
- Confusing a Markdown task-status summary with the designated task authority.
- Saving every brainstorm as a backlog task, or retaining pending discussions after verified materialization.
- Deleting pending context after an unverified external write, or retrying a timed-out create without checking for an existing record.
- Granting implicit permission to deploy simply because the handoff says "next."
- Giving agents general visibility to unrelated private projects.
- Assuming `.gitignore` or a private GitHub setting removes data from existing Git history.

After your first successful cycle, see [Method](METHOD.md) and [Security](SECURITY.md).

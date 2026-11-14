# AI Workspace

**Keep AI-assisted project work understandable across conversations, agents and machines.**

A conversation ends, an agent loses context, or a different model takes over. AI Workspace gives the next contributor a small, Git-backed handoff: where the project stands, which systems are authoritative, what's unresolved, and what needs approval before anything changes.

It's a **method and collection of Markdown templates**, not an app to install. No server, database, framework, task tracker or particular AI model is required.

## Try it in five minutes

1. On GitHub, select **Use this template → Create a new repository**, and make your own workspace **private**. You can also copy the files into a private Git repository you control.
2. Create `projects/<slug>/` and copy [the handoff template](templates/project/HANDOFF.md) to `projects/<slug>/HANDOFF.md`. Fill in the current gate, authoritative sources, last-checked status and the next safe action.
3. Copy [the workspace index example](WORKSPACE.example.md) to `WORKSPACE.md`, replace the fictional project row and keep it private. The foundation ignores this local file by default; you can deliberately track it in your **private** repository.
4. Give a new agent **read-only access to the assigned project only** and ask:

   > Read `AGENTS.md`, `STORAGE.md`, `WORKSPACE.md` and `projects/<slug>/HANDOFF.md`. Identify the current gate, authoritative sources, verified versus reported claims, unresolved questions and the next action requiring approval. Do not modify files, start work or inspect other projects.

5. Compare its answer with the real source or task system. When a useful discussion is paused before formal recording, keep a concise, provisional note in `PENDING.md` and link it from the handoff only if relevant.

For exact setup steps and an exercise, see [Getting started](docs/GETTING_STARTED.md) and the [fictional handoff example](examples/sample-project/README.md).

## A typical private workspace

```text
WORKSPACE.md                  # Private project index and local rules
projects/
  my-project/
    HANDOFF.md                 # Current state and next safe gate
    INFORMATION.md             # Optional: who owns decisions, tasks, evidence
    PENDING.md                 # Optional: valuable unresolved discussions
```

The public repository contains only generic guidance, [templates](templates/project/) and fictional [examples](examples/sample-project/README.md). **Real project directories and private handoffs belong in your private workspace, not in contributions to this upstream repository.**

## Where information belongs

| Information | Authority |
| --- | --- |
| Code and exact revisions | Source repository |
| Tasks, acceptance and statuses | Your designated task/issue system, if any |
| Approved decisions and other durable knowledge | The canonical store assigned to each category; sometimes AI Workspace itself |
| Actual operational state | Running service, database or other operational source |
| Current coordination | `HANDOFF.md`, with links rather than duplicate records |
| Valuable not-yet-recorded discussions | `PENDING.md` until verified materialization or explicit discard |
| Approvals, exceptions and permitted actions | Human operator or explicitly authorized controlling system |

The [information-ownership template](templates/project/INFORMATION.md) helps route categories without creating a second backlog. If a project has no external decision store, it **may** designate its own `IDEAS.md` and `DECISIONS.md` as canonical. A note in a handoff never grants permission to change an authoritative system.

## The working rhythm

**Resume → Verify → Work within scope → Preserve → Publish and verify → Hand off.**

An agent should be able to answer: *What is known? What was merely reported? What has not been checked? What happens next? Who is allowed to do it?*

- Keep the active handoff concise and current. Git history holds previous versions.
- Preserve meaningful unfinished discussions without treating them as approved tasks.
- Verify a new canonical record by reading it back **before** retiring the temporary pending note.
- Attribute tests, reviews and deployments to their evidence. A confident summary is not proof of delivery.
- Limit reads and writes to the explicitly assigned project. Git folders are conventions, **not access-control boundaries**.

See [Method](docs/METHOD.md), [Context lifecycle](docs/CONTEXT_LIFECYCLE.md) and [Security](docs/SECURITY.md).

## What is included?

- [`AGENTS.md`](AGENTS.md) — instructions for agents using a workspace within approved scope.
- [`STORAGE.md`](STORAGE.md) — evidence, provenance, retention and handoff conventions.
- [Project templates](templates/project/) — handoffs, optional routing, pending discussions and local idea/decision registers.
- [External-tracker example](examples/sample-project/README.md) — fictional two-agent review handoff.
- [Local-canonical example](examples/local-only/README.md) — fictional project whose ideas/decisions live in its workspace.
- [Getting started](docs/GETTING_STARTED.md), [Security](docs/SECURITY.md) and [Upstream synchronization](docs/UPSTREAM_SYNC.md).

## Scope, maturity and contributions

**v0.1 foundation:** documentation-first and intentionally small. It has no automatic synchronization, agent orchestration, access isolation, approval enforcement or claim to verify external systems. Adopt the parts that serve your project, and confirm permissions in your actual tools.

Use the [contribution guide](CONTRIBUTING.md) to propose generic improvements. Never include real handoffs, private repository history, credentials or confidential examples in a public contribution. Read the [release checklist](docs/RELEASE_CHECKLIST.md) before publishing a derivative workspace.

Licensed under the [MIT License](LICENSE).

# My Workspace — local configuration example

**Copy this file to `WORKSPACE.md` in your own downstream repository and edit it.** It is intentionally not a list of real projects. The public foundation ignores `WORKSPACE.md` by default; decide explicitly whether to track it in your private downstream repository.

## Project index

| Project | Handoff | Information ownership | External authorities |
| --- | --- | --- | --- |
| Fictional demo (replace this row) | [HANDOFF](examples/sample-project/HANDOFF.md) | [INFORMATION](examples/sample-project/INFORMATION.md) | Fictional tracker, unavailable |

Replace the demo row with a real project under `projects/<slug>/` as you create it. The example above is intentionally browsable before setup.

## Local boundaries

- This working repository is private by default; access is still limited to approved collaborators.
- Only act on a project explicitly assigned in the current request.
- Project-local restrictions override generic storage convenience.
- Never publish project files, history, credentials or artifacts to a public upstream without explicit approval and review.

## Optional integrations

For each project, use optional `INFORMATION.md` to route ideas, decisions, tasks, and research by category. Projects without an external tracker may designate AI Workspace as canonical for some categories. `PENDING.md` is for valuable **not-yet-materialized** conversation context in either case.

List only **safe references** to the real task tracker, source repository or evidence store. Do not record API tokens, login details, personal paths or secrets here.

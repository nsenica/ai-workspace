# Public foundation and private downstream synchronization

**Goal:** Share reusable operating guidance while keeping private project data and history private. Public upstream provides methods, templates and synthetic examples. Private downstream holds actual projects, handoffs, decisions and evidence.

This document describes a **proposed, manual, review-gated process**, not an automatically configured sync. Do **not** apply it to a production workspace without taking a backup and testing the exact tree first.

## Ownership boundary

| Public foundation | Private workspace |
| --- | --- |
| `README.md`, `AGENTS.md`, `STORAGE.md` | `WORKSPACE.md` and personal project index |
| `templates/`, `docs/`, `examples/` | `projects/<slug>/` and project-specific guidance |
| Generic improvements and synthetic tests | Real handoffs, artifacts, evidence and task references |

To reduce future conflicts, prefer adding private instructions in `WORKSPACE.md` or `projects/<slug>/`, rather than editing shared root files directly. Local rules can be stricter than general upstream guidance.

## Two different flows

**Upstream → downstream:** Fetch the public remote into a **private local review branch**; inspect and merge accepted foundational updates. Verify they don't override stricter private rules.

**Downstream → upstream:** Manually distill a generic improvement. Apply it on a **fresh public-history branch** without copying private commits, blobs, branches or artifacts. Review the entire proposed public history before opening a PR.

**Never automate private → public synchronization.**

## First integration with an existing private repo

The two repositories usually have **unrelated Git histories**. Ordinary merge fails without a one-time explicit unrelated-history merge, and duplicate root files require careful conflict resolution.

Before integrating:
1. Wait until the eventual public repository's history is stable. **If the current development repo will be deleted/recreated at launch, defer the real upstream merge until after recreation.** Otherwise a second unrelated-history merge may be necessary.
2. Take a verified private backup and confirm the checkout has no uncommitted or protected changes.
3. In a **new private branch**, extract project-specific README/index content into a private `WORKSPACE.md` and project-local files. Preserve existing records and history.
4. Inspect the public foundation's root files and select the intended shared versions without discarding private rules.
5. Configure a dedicated public remote as **fetch-only** when practical. Check the active push destinations.

A possible *manual review sequence*, run inside the existing private checkout:

```sh
git status --short
git remote -v
git switch -c chore/adopt-ai-workspace

# After separately committing the private WORKSPACE.md migration:
git remote add ai-workspace https://github.com/OWNER/ai-workspace.git
git fetch ai-workspace main

# One-time explicit integration of independent histories:
git merge --allow-unrelated-histories --no-ff --no-commit ai-workspace/main

# Expect add/add conflicts for README.md / AGENTS.md / STORAGE.md.
# Resolve deliberately; do not blindly select one side.
git status
git diff --check
# Inspect every staged file and any conflict markers before committing.
```

If the merge is unsafe, use `git merge --abort` before committing. After all conflicts are resolved, explicitly stage approved files, create a merge commit, and review the diff and resulting tree before pushing **only to the private remote**. Avoid running these commands against a live/dirty checkout without an operator-approved migration plan.

After a completed one-time merge, both repositories share ancestry. Subsequent accepted upstream changes generally use an ordinary `git fetch ai-workspace` followed by `git merge --no-ff ai-workspace/main` **on a private review branch**, with regular conflict review.

## Do not mistake merged ancestry for publication safety

An ordinary downstream merge preserves both histories in the **private** repository. It is suitable for adopting a public baseline privately.

It is **not suitable for contributing the downstream branch back to upstream**: that would risk publishing all reachable private history. Public contributions must start from clean upstream history.

## Suggested adoption acceptance checks

- Shared root guidance is readable and project-independent.
- Actual project files and private workspace configuration are unchanged or deliberately migrated.
- Agent access, task authority and operational permissions did not expand.
- A new read-only agent can still identify the correct next gate for each sampled project.
- Only the intended private Git remote received the integration commit.

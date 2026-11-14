# Public foundation and private downstream synchronization

**Purpose:** Share generic AI Workspace improvements while keeping actual project context, decisions, conversations and evidence in a separate **private** downstream repository.

There is no built-in synchronization. Every update is a deliberate, review-gated Git operation. Never configure automatic private-to-public publication.

## Separate what each repository owns

| Public upstream | Private downstream |
| --- | --- |
| `README.md`, `AGENTS.md`, `STORAGE.md` | Project-specific rules and index (`WORKSPACE.md`) |
| `templates/`, `docs/`, `examples/` | Actual `projects/<slug>/` handoffs, pending context and evidence |
| Generic, synthetic and approved improvements | Real project history, access decisions and sensitive records |

Keep downstream customizations in project folders or `WORKSPACE.md` where possible to reduce conflicts with future upstream releases. Repository visibility and directory names alone do not enforce per-project permissions.

## First: determine whether histories are related

There are at least three legitimate ways to create a private workspace:

1. **Clone and push** the public repository to a private remote: Git ancestry is retained.
2. **Use GitHub's template feature** to create a new private repository: it normally starts with an independent initial commit, even when the files match.
3. **Adopt the foundation into an older private workspace:** histories may be unrelated.

Never assume shared ancestry from identical file contents. Inspect the commits and use `git merge-base` when deciding on the integration strategy. A freshly republished public foundation can have different Git history from an older private workspace even when its files are identical.

## Public → private: controlled adoption

1. Back up the downstream repository, confirm the private checkout is clean and check its remotes.
2. From the private checkout, fetch the public upstream into a **private review branch**, never an automated merge to a production workspace.
3. Compare root guidance and templates. Preserve local authority, reader access, agent scope, pending context and all real project files.
4. If the repositories share ancestry, use an ordinary reviewed merge (or manually apply selected changes).
5. If their histories are unrelated, either copy selected reviewed generic files **without importing public history**, or perform a one-time reviewed unrelated-history merge **into the private repository only**.
6. Inspect the staged tree, resolve conflicts deliberately, run the relevant read-only continuation checks, then publish **only to the private remote** after approval.

Example for an existing private checkout (review commands; they do not publish):

```sh
git status --short
git remote -v
# Add the public upstream as a distinct remote only if not already configured:
git remote add ai-workspace https://github.com/OWNER/ai-workspace.git
git fetch ai-workspace main

git switch -c chore/review-ai-workspace-update

git merge-base HEAD ai-workspace/main || echo 'Unrelated history: choose a deliberate integration method'

git diff --stat HEAD ai-workspace/main  # Review the potentially large difference
```

For a **shared-ancestry** private branch, after reviewing the changes and with a safe clean checkout, a normal `git merge --no-ff --no-commit ai-workspace/main` can stage integration for inspection.

For an **unrelated-history** private branch, `git merge --allow-unrelated-histories --no-ff --no-commit ai-workspace/main` is an option only when expressly approved, with a verified backup and intentional conflict resolution. Existing root files may produce add/add conflicts. If uncertain, prefer copying only the reviewed generic changes. Use `git merge --abort` if the resulting merge is unsafe.

**Never run the reverse operation:** merging the private downstream into public upstream would make private history reachable from public Git.

## Private → public: reauthor generic improvements

1. Describe the useful method or template improvement without copying real project context.
2. Create a new branch from the **public** upstream, not from downstream history.
3. Reimplement the generic change using synthetic examples and a privacy-safe author/committer identity.
4. Review every staged file and every commit that will become public. A cherry-pick can preserve original author metadata, so do not treat cherry-picking private commits as safe by default.
5. Open a focused public pull request for review.

Do **not** push a private branch, merge private history upstream, upload private archives or enable an automated private-to-public sync.

## Acceptance checks

- The target private project index and handoffs remain intact.
- No private content, logs, credentials or personal metadata enter public upstream.
- New shared guidance is compatible with the private project's stricter scope rules.
- A fresh read-only agent can identify the next safe gate for a sampled project.
- The only repository receiving the downstream integration is the intended **private** remote.

See [Security](SECURITY.md) and [Getting started](GETTING_STARTED.md).

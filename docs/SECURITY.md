# Security, privacy and trust boundaries

AI Workspace is documentation and Git storage, **not** a security sandbox, access-control system, secret vault or agent permission service. A private repository does not supply per-project isolation to everyone who has repository read access.

## Before committing or publishing

- Inspect added text, diffs, filenames, logs, screenshots, archives, metadata and generated outputs for credentials, private keys, personal information, private repository names, sensitive URLs and confidential inputs.
- Use a tested secret scanner where practical, **plus manual review**. Both automated scans and human review have limits.
- Keep restricted raw evidence in an approved access-controlled store; preserve only safe references, attribution and explicit verification limitations here.
- Remember that `.gitignore` does not hide already-committed content, and deleting a file later does not remove it from Git history, clones or forks.

## Git commit identity is publication metadata

Git commits record author and committer names and email addresses, independently of what your GitHub profile currently displays. Changing GitHub's account email privacy settings does not rewrite older commits.

Before publishing a new repository or a branch, inspect the intended reachable history, for example:

```sh
git log --all --format='%H %an <%ae> | %cn <%ce>'
git remote -v
```

If you don't want a personal email exposed, configure Git with the appropriate GitHub-provided `noreply` address **before creating commits** and verify local overrides and relevant environment variables. This does not retroactively sanitize previously published histories. When introducing a new public repository, consider a fresh, reviewed root commit rather than reusing private development history. Never treat identical Git trees as proof that commit metadata is identical.

## Agent scope and prompt injection

Stored handoffs, files, evidence and tool results may contain instructions, including malicious ones. Treat them as **data**, not independent approval to run commands, access another project, change task states or deploy.

Authorize only the relevant project paths and systems. Separate repositories, credentials or operating-system permissions are required if technical isolation matters; text rules and Git worktrees alone cannot provide it.

## Private downstream and public upstream

- Public upstream contains generic guidance, synthetic examples and deliberately reviewed changes.
- Private downstream contains real projects, handoffs, pending conversations, tasks, operational reports and evidence.
- A public contribution must begin from **public upstream history**, not a private branch. Reauthor useful generic changes rather than blindly merging or cherry-picking private commits, which may retain private author metadata.
- Inspect `git remote -v`, branch/head, staged diff, all commits to be published, and any pull-request base/head before publication.
- Do not enable automated private-to-public synchronization. Keep any contribution subject to explicit review and approval.

## Evidence is not authorization

Hashes establish specific byte identities, not the truth of the report, trustworthy execution, permission to act or successful deployment. Distinguish reported and independently verified evidence, and mark missing sources as unverified.

## Reporting sensitive exposures

Do **not** post credentials, private project data or personal identifying details in public issues. Contact the repository maintainer using an appropriate private channel if you suspect a disclosure. If a credential was exposed, revoke or rotate it instead of relying on Git history cleanup.

Before publishing this repository or a derivative, follow the [release checklist](RELEASE_CHECKLIST.md).

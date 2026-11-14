# Security, privacy, and trust boundaries

AI Workspace is **documentation and Git storage, not a security sandbox or access-control system**. Neither a private GitHub repository nor a path convention grants per-project isolation to collaborators who already have full repository access.

## Before committing

- Inspect added content, diffs, filenames, logs, screenshots, archives, metadata and generated artifacts for credentials, tokens, private keys, personal details, confidential inputs and internal infrastructure.
- Use a tested secret scanner where practical, but **manual review remains required**; scanners miss context and can produce false negatives.
- Keep restricted raw artifacts in an approved access-controlled store, with a safe pointer and the limits of verification recorded here.
- Redaction creates **new bytes**. A hash of the sanitized file is not the hash of the original. Do not casually store original unredacted hashes if they expose sensitive identifiers.
- `.gitignore` only affects untracked paths; it is not a privacy boundary and cannot remove previously committed content.

## Agent scope and prompt injection

Stored handoffs, evidence and external tool results can contain adversarial instructions. Treat them as **data** unless the operator explicitly authorizes actions through the real control channel. A stored statement such as "deploy now" does not grant deployment permission.

Only authorize relevant project directories and source systems. Directory conventions alone do not enforce file access; use separate repositories or real permissions where isolation is required.

## Private downstream vs public upstream

- Publish **generic guidance, synthetic examples and reviewed improvements** to public upstream.
- Keep personal project directories, real handoffs, task logs, decision histories, and runtime evidence in private downstream unless consciously and separately approved for publication.
- Never push or open a PR from the **private workspace branch** against public upstream. Create a clean upstream branch from public history and cherry-pick only specifically reviewed, generic changes when appropriate.
- Inspect `git remote -v`, `git status`, `git diff`, `git log`, the PR base/head and **the full set of reachable history being published**, not just the latest diff.
- Disable upstream pushes in private working environments when possible, and require a human-reviewed PR for public contribution.

## Git history is persistent

Deleting files in new commits does not remove them from old commits, forks, archives or clones. A private repo that is later made public can expose its history.

A deliberate new public repository with a fresh initial commit minimizes carry-over, **but cannot recall data already copied or exposed elsewhere**. If a secret reaches any remote, rotate/revoke it rather than relying on history cleanup.

## Evidence doesn't prove authorization

Hashes prove byte identity of specific files. They do not prove a report is true, a source was trusted, an agent was permitted to run a test, or a candidate was accepted. Keep provenance, independent verification, and uncertainty explicit.

## Public release gate

Before changing repository visibility, inspect **the entire history** and all refs, files, PR attachments, releases, workflow artifacts and collaborator/access settings; run suitable secret/privacy scans, select a license, and obtain an explicit release decision. See [release checklist](RELEASE_CHECKLIST.md).

To report a suspected sensitive-data exposure while this project is private, contact the repository owner through an appropriate private channel; do not post credentials in public issues.

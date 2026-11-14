# Contributing to AI Workspace

AI Workspace is a small, tool-agnostic documentation project. Contributions should make the method clearer, safer, easier to adopt or easier to verify, without introducing required infrastructure.

## Good contributions

- Improve a confusing instruction, handoff template, information-ownership rule or context-lifecycle example.
- Fix a broken link, contradiction, security boundary or misleading evidence claim.
- Add a **fictional**, bounded acceptance scenario that demonstrates why the change helps.

Avoid adding mandatory services, frameworks or project-management abstractions without a clearly demonstrated need.

## Before proposing changes

1. Start from the **public upstream** default branch. Never use your private workspace as the source branch for a public pull request.
2. Explain the problem, proposed change, and compatibility implications for existing private workspaces.
3. Use synthetic data only. Do not include real project handoffs, archived conversations, private URLs, credentials, internal file paths or logs.
4. Check relative Markdown links, template placeholders, Git metadata and the complete commits you intend to publish.
5. Preserve authority boundaries: stored context is not permission to create tasks, change decisions, run agents or deploy.
6. Open a focused pull request for human review; do not claim checks or independent review you did not perform.

**Private-to-public safety:** Do not merge a private project branch into this repository, and do not assume cherry-picking a private commit is safe: it may carry its original author metadata as well as private content. Reauthor any transferable generic improvement as a new reviewed patch on clean public history, with your intended public Git identity.

See [Security](docs/SECURITY.md), [Upstream synchronization](docs/UPSTREAM_SYNC.md) and the [release checklist](docs/RELEASE_CHECKLIST.md).

## Expectations

This repository has no guaranteed response or maintenance schedule. Proposals are evaluated for clarity, usefulness, scope and privacy. Keep changes small and acknowledge limitations. Documentation and templates are provided under the [MIT License](LICENSE); by submitting a contribution, you agree to contribute it on those terms.

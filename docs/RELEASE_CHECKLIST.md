# Public-release checklist

Use this checklist for the initial public release **and** for future publication of changes that could expose private material. It is an operational checklist, not permission to change repository visibility or publish.

## Identity, license and scope

- [ ] Confirm the product name, intended audience and truthful README status.
- [ ] Include an approved explicit license (`LICENSE`) and align contribution language.
- [ ] Inspect Git author **and committer** names/emails across all commits and refs proposed for publication. Use a public-safe identity if desired.
- [ ] Confirm the repository contains only generic guidance and synthetic examples; no real project handoffs or private workspace index.

## Privacy and history

- [ ] Audit **all reachable commits**, branches, tags, PR histories, releases and workflow artifacts that will become public—not only the current file tree.
- [ ] Review contents, filenames, URLs, fixtures, generated artifacts and metadata for credentials, personal email addresses, internal infrastructure and confidential context.
- [ ] Run an appropriate secret scanner where practical, and perform a manual review; no scanner proves the absence of sensitive data.
- [ ] Confirm no private project branch/history is merged into the public repository and no automatic private-to-public push is configured.

## Usability and compatibility

- [ ] Validate relative Markdown links and illustrative JSON/templates.
- [ ] Test a fresh clone or template-derived **private** workspace with at least one fictional project, including optional `INFORMATION.md` and `PENDING.md`.
- [ ] Ask a fresh read-only reviewer/agent to identify the next gate, reported vs verified claims and authorization boundaries without seeing the previous discussion.
- [ ] Test upstream → private downstream adoption on a disposable checkout, accounting for related and unrelated Git histories. Never push downstream commits upstream.
- [ ] Review contribution expectations, security guidance and GitHub repository settings, including the template option if desired.

## Publication gate

- [ ] Independently review the exact intended public commit/tree and verify it against the release candidate.
- [ ] Obtain **explicit owner go/no-go** for making the repository public.
- [ ] After publication, check actual visibility, repository files, history, license display, template behavior and external onboarding instructions.

If any check fails or cannot be established, preserve the limitation and do not claim that check passed. Keep the repository private until the owner authorizes publication.

# Getting started

AI Workspace is a method and Markdown file structure, not software to install. Basic Git familiarity is helpful, but no AI vendor, framework or task tracker is required.

## 1. Create a private workspace

From the GitHub repository, select **Use this template → Create a new repository** if the template option is enabled. Choose **Private**. Alternatively, copy the reviewed files into a new private Git repository you control.

Before uploading your own data, check the destination remote, repository visibility, account permissions and commit author email. See [Security](SECURITY.md).

## 2. Add one project

In your new private workspace, choose a simple lowercase slug (for example `notes-demo`), then create its handoff:

```sh
mkdir -p projects/notes-demo
cp templates/project/HANDOFF.md projects/notes-demo/HANDOFF.md
cp templates/project/INFORMATION.md projects/notes-demo/INFORMATION.md
cp WORKSPACE.example.md WORKSPACE.md
```

Edit `projects/notes-demo/HANDOFF.md` so it explains the project's **real or deliberately fictional** current state, what has been checked, and the next safe action. If the project uses an external task tracker, make `INFORMATION.md` point to it rather than duplicating task records. If no external store exists, you may designate project-local `IDEAS.md` and `DECISIONS.md` as canonical for particular categories. Don't treat those files as automatic authority to implement or approve anything.

Replace the example row in `WORKSPACE.md` with your project. The foundation's `.gitignore` excludes the root `WORKSPACE.md` by default to avoid accidental contribution upstream. You can deliberately track it in **your private repository** with `git add -f WORKSPACE.md` after reviewing the file and remote.

## 3. Try a read-only fresh-agent handoff

Give a new chat or agent access only to the assigned project and relevant generic guidance, then use this instruction:

> You are working on project `notes-demo`. Your assignment is **read-only analysis**; do not write, execute, create tasks or change settings. Read `AGENTS.md`, `STORAGE.md`, `WORKSPACE.md` (if present), and `projects/notes-demo/HANDOFF.md` and `INFORMATION.md`. State the authoritative stores, current gate, reported versus independently verified claims, open questions and next step that would require approval. If an external system cannot be inspected, say so. Do not inspect other projects.

Check that the answer doesn't claim nonexistent tests, source access or approvals. For a completely fictional controlled example, see [sample project](../examples/sample-project/README.md).

## 4. Preserve a discussion before it becomes canonical (optional)

If you explore an idea and defer registering it, create `projects/notes-demo/PENDING.md` from the [pending template](../templates/project/PENDING.md) when you have permission to write coordination context. Summarize motivation, findings, open questions, what is not approved, revisit trigger and intended canonical destination. Do not copy a full transcript or treat a discussion as an accepted task.

Later, if an authorized actor writes the idea or decision to its designated store, **read it back** and verify the identity/content before retiring the redundant pending note. If the write fails or cannot be checked, preserve the unresolved portion. See [Context lifecycle](CONTEXT_LIFECYCLE.md).

## 5. Complete a handoff cycle

1. Start with a known source/task revision or an explicitly local scope, and verify mutable facts through permitted channels.
2. Work only within the current assignment; requesting a handoff is not permission to deploy or mutate a tracker.
3. Preserve the next gate and relevant references in `HANDOFF.md`; avoid an ever-growing chronological log.
4. Check the diff for confidentiality, attribution and permissions, commit to the intended **private** remote, and verify the published commit.
5. Open a fresh read-only session; ask it to identify the next safe action and compare with the real authoritative system.

## Beginner pitfalls

- Uploading private project context or history to public upstream.
- Treating a handoff claim as independent verification of a test, review or deployment.
- Creating duplicate task/decision registers when another system owns them.
- Erasing pending discussions after an unverified write, or retrying a create without checking whether a record exists.
- Using directory conventions as security isolation or inferring permission to act from stored text.
- Assuming `.gitignore`, GitHub email privacy settings or a new file deletion removes old Git history.

See [Method](METHOD.md), [Security](SECURITY.md) and [Upstream synchronization](UPSTREAM_SYNC.md).

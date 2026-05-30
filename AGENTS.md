# Agent Operating Rules

This checkout is the complete working tree for one project only.

Project: `trocr_small_korean_finetune`
Local root: `/Users/twentyflags/twentyflags/knocklab/04.작업/git/trocr_small_korean_finetune`
Allowed working branch: `main`
Primary remote: `origin`
Primary remote URL: `https://github.com/atozwizard/trocr_small_korean_finetune.git`
Backup remote: `backup`
Backup remote URL: `ssh://git@210.113.0.140:2345/home/git/projects/twentyflags.git`
Backup ref: `projects/trocr_small_korean_finetune/main`

## Mental Model

- GitHub is the canonical project repository.
- The server bare repo is only a backup target.
- `origin/main` is the normal source of truth for daily work.
- `backup/projects/trocr_small_korean_finetune/main` is a copy of this project's `main`, stored inside the shared server bare repo.
- Other `projects/*/main` refs in the backup remote belong to other projects and must not be merged, edited, or pushed from this checkout.

## Start Every Task With These Checks

Run these before reading broadly, editing files, committing, or pushing:

```bash
git rev-parse --show-toplevel
git branch --show-current
git status --short
git remote -v
git config --get-all remote.backup.fetch
```

Expected values:

```text
top-level: /Users/twentyflags/twentyflags/knocklab/04.작업/git/trocr_small_korean_finetune
branch: main
origin: https://github.com/atozwizard/trocr_small_korean_finetune.git
backup: ssh://git@210.113.0.140:2345/home/git/projects/twentyflags.git
backup fetch: +refs/heads/projects/trocr_small_korean_finetune/main:refs/remotes/backup/projects/trocr_small_korean_finetune/main
```

If any value does not match, stop and report the mismatch. Do not "fix" remotes, branches, or refs unless the user explicitly asks for that repair.

## Workspace Boundaries

- Treat this repository root as the entire project.
- Do not create sibling project directories inside this checkout.
- Do not edit files outside this repository root.
- Do not read or reason over sibling project code unless the user explicitly asks for a cross-project comparison.
- Do not create nested Git repositories.
- Do not run `git init` inside subdirectories.
- Do not add submodules or worktrees unless the user explicitly asks.
- Do not move this checkout into another repository.

## Normal Git Workflow

For ordinary code or documentation work:

```bash
git status --short
git diff
git add <intended files>
git commit -m "<clear message>"
git push origin main
```

Only commit and push when the user asks for repository changes to be saved or published, or when the current task is explicitly repository setup/maintenance. If the user only asks for analysis or review, do not commit.

## Backup Workflow

Use the backup remote only when the user asks for a server backup, or when the task is explicitly about keeping the server backup in sync.

```bash
git push backup HEAD:projects/trocr_small_korean_finetune/main
```

Never use plain `git push backup` unless you have verified that the upstream and refspec point exactly to `projects/trocr_small_korean_finetune/main`.

## Allowed Git Commands

- `git status`
- `git diff`
- `git log`
- `git remote -v`
- `git fetch origin`
- `git pull --ff-only origin main`
- `git add <intended files>`
- `git commit -m "<message>"`
- `git push origin main`
- `git push backup HEAD:projects/trocr_small_korean_finetune/main`

## Forbidden Git Commands And Actions

- Do not switch to `projects/*` branches in this checkout.
- Do not merge or rebase from backup refs.
- Do not push to `master`.
- Do not push to a backup ref other than `projects/trocr_small_korean_finetune/main`.
- Do not run `git push --all`.
- Do not run `git push --mirror`.
- Do not force push unless the user explicitly asks and confirms the target.
- Do not delete local or remote branches or tags unless the user explicitly asks.
- Do not edit remote URLs unless the user explicitly asks.
- Do not run destructive cleanup such as `git reset --hard` or `git clean -fd` unless the user explicitly asks.

## Pre-Push Hook

This checkout should have `.git/hooks/pre-push` installed.

The hook is expected to allow only:

```text
main -> origin/main
main -> backup/projects/trocr_small_korean_finetune/main
```

If a push is blocked, inspect the command and target. Do not bypass the hook with `--no-verify` unless the user explicitly asks and the target has been checked.

## When Creating Files

- Keep project-specific files in this checkout.
- Keep repository policy in `AGENTS.md`.
- Keep human-facing notes in `readme.md` or other project docs.
- Avoid committing generated artifacts, large datasets, model weights, caches, or local secrets unless the user explicitly asks and the repository policy allows it.

## Handoff Summary Expectations

When finishing work in this checkout, tell the user:

- which branch was changed;
- whether changes were pushed to GitHub;
- whether changes were backed up to the server;
- any commands that failed or were intentionally skipped.


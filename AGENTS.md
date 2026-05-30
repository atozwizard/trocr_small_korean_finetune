# Agent Rules

This checkout is a single project workspace.

Project: trocr_finetune
Allowed branch: projects/trocr_finetune/main
Allowed remote: ssh://git@210.113.0.140:2345/home/git/projects/twentyflags.git

## Boundaries

- Treat this repository root as the entire project.
- Do not create sibling projects inside this checkout.
- Do not access, edit, or reason over files outside this repository root.
- Do not use nested Git repositories, submodules, or `git init` inside subdirectories.

## Git Rules

Before making changes, verify:

```bash
git rev-parse --show-toplevel
git branch --show-current
git status --short
```

The current branch must be:

```text
projects/trocr_finetune/main
```

Allowed Git operations:

- `git status`
- `git diff`
- `git add`
- `git commit`
- `git pull --ff-only`
- `git push origin HEAD:projects/trocr_finetune/main`

Forbidden Git operations:

- Switching to another project branch
- Merging another project branch
- Pushing to `main`, `master`, or another `projects/*` branch
- `git push --all`
- `git push --mirror`
- Editing remote URLs
- Deleting branches or tags


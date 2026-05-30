# Agent Rules

This checkout is a single project workspace.

Project: trocr_small_korean_finetune
Allowed branch: main
Primary remote: https://github.com/atozwizard/trocr_small_korean_finetune.git
Backup remote: ssh://git@210.113.0.140:2345/home/git/projects/twentyflags.git
Backup ref: projects/trocr_small_korean_finetune/main

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
main
```

Allowed Git operations:

- `git status`
- `git diff`
- `git add`
- `git commit`
- `git pull --ff-only`
- `git push origin main`
- `git push backup HEAD:projects/trocr_small_korean_finetune/main`

Forbidden Git operations:

- Switching to another project branch
- Merging another project branch
- Pushing directly to server refs other than `projects/trocr_small_korean_finetune/main`
- Pushing to `master` or another `projects/*` branch
- `git push --all`
- `git push --mirror`
- Editing remote URLs
- Deleting branches or tags

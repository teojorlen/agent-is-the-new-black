# Agent Context — `<repo-name>`

<!--
  INSTRUCTIONS FOR REPO OWNERS
  ─────────────────────────────
  Copy this file to .github/agent-context.md in your repository.
  Fill in every section. Remove sections that do not apply.
  Agents in this pack will read this file before doing any work.
-->

## Project overview

<!-- One or two sentences describing what this project is and does. -->

**Name:** `<repo-name>`  
**Description:** _TODO_  
**Primary language(s):** _TODO_ (e.g. TypeScript, Python, Go)  
**Framework(s):** _TODO_ (e.g. Next.js, FastAPI, Rails)

---

## Directory layout

<!--
  List key directories and what they contain.
  Example:
  - src/       Application source code
  - src/api/   REST API handlers
  - src/ui/    Frontend components
  - tests/     Automated tests
  - docs/      Architecture and design documents
  - infra/     IaC / deployment scripts
-->

```
<repo-name>/
├── _TODO_/     # description
├── _TODO_/     # description
└── _TODO_/     # description
```

---

## Documentation pointers

<!--
  Tell agents where to find key documents.
  Examples:
  - Architecture: docs/architecture.md
  - API contract: docs/api.md
  - Project plan: docs/project-plan.md
  - ADRs: docs/adr/
-->

| Document | Path |
|---|---|
| Architecture overview | `_TODO_` |
| Project plan / roadmap | `_TODO_` |
| ADR directory | `_TODO_` |
| API contract | `_TODO_` |

---

## Commands

<!--
  Replace every _TODO_ with the exact shell command.
  These are used by Developer, Quality, and Orchestrator agents.
-->

```yaml
install_command:   _TODO_    # e.g. npm install
build_command:     _TODO_    # e.g. npm run build
dev_command:       _TODO_    # e.g. npm run dev
test_command:      _TODO_    # e.g. npm test
lint_command:      _TODO_    # e.g. npm run lint
pre_merge_checks:            # additional gates before a PR is merged
  - _TODO_                   # e.g. npm run typecheck
  - _TODO_                   # e.g. npm run test:e2e
```

---

## Container / services setup

<!--
  Describe how to start any required services (databases, queues, etc.).
  Leave this section blank if the project has no external services.
-->

**Compose file:** `_TODO_` (e.g. `docker-compose.yml`)  
**Start services:** `_TODO_` (e.g. `docker compose up -d`)  
**Stop services:** `_TODO_` (e.g. `docker compose down`)  
**Compose project naming:** `_TODO_` (e.g. `<repo>-task-<issue-number>` for worktrees)

---

## Branch and worktree conventions

```yaml
base_branch:         main            # branch PRs are opened against
branch_prefix:       feat/           # e.g. feat/issue-42-short-desc
worktree_prefix:     ../<repo>-task- # e.g. ../myrepo-task-42
```

---

## CI configuration

<!--
  Describe CI checks that must pass.
  Point to workflow files if relevant.
-->

**CI provider:** _TODO_ (e.g. GitHub Actions)  
**Workflow files:** `.github/workflows/`  
**Required checks before merge:**

- _TODO_ (e.g. `ci / test`)
- _TODO_ (e.g. `ci / lint`)

---

## Coding conventions

<!--
  List any project-specific conventions agents must follow.
  Examples:
  - Use conventional commits (feat:, fix:, chore:, docs:, etc.)
  - All public functions must have docstrings
  - Prefer composition over inheritance
-->

- _TODO_
- _TODO_

---

## Cleanup instructions

<!--
  Steps agents must take after completing a task.
  Examples:
  - Remove the git worktree: git worktree remove ../<repo>-task-<N>
  - Stop compose services: docker compose -p <repo>-task-<N> down -v
  - Delete the feature branch after PR is merged
-->

1. _TODO_
2. _TODO_

# agent-is-the-new-black

> A pack of well-dressed agents with dark sunglasses. One of them is probably named Smith.

A reusable, generic **Copilot agent pack** for software development teams. Drop it into any repository via `git subtree` and get a set of coordinated AI agents that handle planning, implementation, review, architecture, and quality — all driven by a lightweight per-repo configuration file.

---

## What this is

This pack provides six specialist agents designed to work together on development tasks:

| Agent | Role |
|---|---|
| **Orchestrator** | Breaks down issues, delegates to specialists, manages worktrees, opens PRs |
| **Developer** | Implements features and fixes, writes tests |
| **Reviewer** | Reviews pull requests for correctness, security, and style |
| **Architect** | Evaluates technical design, proposes architecture, writes ADRs |
| **Quality** | Runs lint, build, and test suites; reports quality gate results |
| **Product Owner** | Clarifies requirements, writes acceptance criteria, validates deliverables |

The agents are **project-agnostic**. They read all project-specific information (commands, directory layout, conventions, docs pointers) from a single context contract file that lives in the consuming repository.

---

## Directory layout

```
agent-is-the-new-black/
├── agents/                     # Agent definition files
│   ├── orchestrator.agent.md   # Coordinator agent
│   ├── developer.agent.md      # Implementation agent
│   ├── reviewer.agent.md       # Code review agent
│   ├── architect.agent.md      # Architecture agent
│   ├── quality.agent.md        # Quality gate agent
│   └── product_owner.agent.md  # Requirements & validation agent
├── templates/
│   └── agent-context.md        # Per-repo context contract template
└── README.md
```

---

## How to adopt

### 1. Add this pack to your repository via `git subtree`

```bash
# One-time: vendor the pack into your repo under .github/agent-pack/
git subtree add \
  --prefix .github/agent-pack \
  https://github.com/teojorlen/agent-is-the-new-black.git \
  main --squash
```

The agent files will live at `.github/agent-pack/agents/`.

### 2. Copy the agents to `.github/agents/`

GitHub Copilot picks up agent definitions from `.github/agents/`. Copy or symlink:

```bash
cp .github/agent-pack/agents/*.agent.md .github/agents/
```

(Or configure your editor/tooling to point at the pack path directly.)

### 3. Create your context file

Copy the template and fill it in:

```bash
cp .github/agent-pack/templates/agent-context.md .github/agent-context.md
```

Open `.github/agent-context.md` and replace every `_TODO_` placeholder with your project's real values. See [How to customize](#how-to-customize) below.

### 4. Updating the pack later

Pull upstream changes with:

```bash
git subtree pull \
  --prefix .github/agent-pack \
  https://github.com/teojorlen/agent-is-the-new-black.git \
  main --squash
```

---

## How to customize

All project-specific configuration lives in `.github/agent-context.md` (in the **consuming** repo — not in this pack). The agents will read this file before doing any work.

The context file covers:

- **Project overview**: name, description, language, framework
- **Directory layout**: where source, tests, docs, and infra live
- **Documentation pointers**: architecture doc, ADR directory, project plan
- **Commands**: install, build, dev, test, lint, pre-merge checks
- **Container/services**: compose file, start/stop commands, project naming for worktrees
- **Branch and worktree conventions**: base branch, branch prefix, worktree naming pattern
- **CI configuration**: provider, workflow files, required checks
- **Coding conventions**: commit style, documentation requirements, etc.
- **Cleanup instructions**: how to tear down worktrees and services after a task

If a section doesn't apply to your project (e.g., no Docker services), simply remove it from your context file.

---

## Contributing

Improvements to the generic agents are welcome. Keep changes backwards-compatible and project-agnostic. Never add project-specific references to agent files in this repo.


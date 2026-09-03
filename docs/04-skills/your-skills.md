# Your Installed Skills

This is the complete list of skills in your OpenCode setup as of the course setup. You have **51 skills** across two sources.

---

## Superpowers Package — 14 skills

Located at: `%USERPROFILE%\.config\opencode\node_modules\superpowers\skills\`

These are production-ready process skills that ship with the `superpowers` npm package.

| Skill | When it fires |
|-------|--------------|
| `using-superpowers` | Every session — the master router that auto-invokes all other skills |
| `brainstorming` | Before any creative work — features, components, new functionality |
| `systematic-debugging` | When you report a bug, say "debug this", or something is broken/slow |
| `test-driven-development` | When implementing any feature or bugfix, before writing code |
| `writing-plans` | When you have a spec and need a step-by-step implementation plan |
| `executing-plans` | When you have a written plan to execute with review checkpoints |
| `subagent-driven-development` | When executing plans with independent tasks in the current session |
| `dispatching-parallel-agents` | When 2+ tasks can run independently without shared state |
| `using-git-worktrees` | Before feature work that needs isolation from the current workspace |
| `finishing-a-development-branch` | When implementation is complete and you need to integrate work |
| `receiving-code-review` | When processing review feedback — prevents blind implementation |
| `requesting-code-review` | Before merging — self-review to verify work meets requirements |
| `verification-before-completion` | Before claiming work is done — runs verification commands first |
| `writing-skills` | When creating or editing skill files |

---

## Custom Skills — 37 skills

Located at: `%USERPROFILE%\.agents\skills\`

### Planning & Design

| Skill | What it does |
|-------|-------------|
| `brainstorming` | Explore user intent and requirements before implementation |
| `wayfinder` | Plan a huge chunk of work as a map of decision tickets |
| `to-spec` | Turn a conversation into a spec on the issue tracker |
| `to-tickets` | Break a plan into tracer-bullet tickets with blocking edges |
| `to-questionnaire` | Turn a decision into a questionnaire for someone else |
| `prototype` | Build a throwaway prototype to answer a design question |
| `loop-me` | Grill you about specs for workflows you want to build |

### Code Quality & Review

| Skill | What it does |
|-------|-------------|
| `code-review` | Review changes since a commit along Standards + Spec axes, in parallel |
| `tdd` | Test-driven development — red-green-refactor workflow |
| `codebase-design` | Shared vocabulary for designing deep modules and clear interfaces |
| `improve-codebase-architecture` | Scan for deepening opportunities, present as HTML report |
| `setup-ts-deep-modules` | Wire dependency-cruiser into a TypeScript repo for deep modules |
| `migrate-to-shoehorn` | Migrate `as` type assertions to `@total-typescript/shoehorn` |

### Debugging & Diagnosis

| Skill | What it does |
|-------|-------------|
| `diagnosing-bugs` | Structured diagnosis loop for hard bugs and performance regressions |
| `resolving-merge-conflicts` | Resolve in-progress git merge/rebase conflicts |
| `git-guardrails-claude-code` | Set up hooks to block dangerous git commands before they execute |

### Implementation

| Skill | What it does |
|-------|-------------|
| `implement` | Implement a piece of work based on a spec or tickets |
| `implement-spec` | Implement a specification in code |
| `tdd` | Build features test-first |
| `scaffold-exercises` | Create exercise directories with sections, problems, and solutions |
| `setup-pre-commit` | Set up Husky pre-commit hooks with lint-staged, type checking, tests |

### Domain & Documentation

| Skill | What it does |
|-------|-------------|
| `domain-modeling` | Build and sharpen a project's domain model, write CONTEXT.md |
| `research` | Investigate against primary sources, capture findings as Markdown |
| `setup-matt-pocock-skills` | Configure repo for engineering skills (issue tracker, labels, docs) |

### Thinking & Critique

| Skill | What it does |
|-------|-------------|
| `grilling` | Relentlessly interview you about a plan or decision |
| `grill-me` | Sharpen a plan or design through hard questions |
| `grill-with-docs` | Relentless interview + creates ADRs and glossary as you go |
| `ask-matt` | Router — asks which skill fits your situation |
| `retro` | Conduct a retrospective on a coding session |

### Session Management

| Skill | What it does |
|-------|-------------|
| `handoff` | Compact the conversation into a handoff doc for another agent |
| `claude-handoff` | Hand off to a fresh background agent that picks up immediately |
| `wait-what` | Re-pitch the last message that didn't land |

### Teaching & Writing

| Skill | What it does |
|-------|-------------|
| `teach` | Teach the user a new skill or concept |
| `writing-for-agents` | Write skills, AGENTS.md, CLAUDE.md documents |
| `writing-beats` | Assemble raw material into a journey of beats |
| `writing-fragments` | Mine raw writing fragments — no structure yet |
| `writing-shape` | Shape raw material into an article paragraph by paragraph |

### Guided Wizards

| Skill | What it does |
|-------|-------------|
| `wizard` | Generate an interactive wizard for steps only a human can perform |

---

## How to invoke any skill

**Explicit invocation:**
```
skill brainstorming
use the code-review skill
```

**Auto-invocation:**  
The `using-superpowers` skill routes automatically. Say "fix this bug" and `systematic-debugging` fires before OpenCode touches any code.

!!! tip "When in doubt, ask `ask-matt`"
    Not sure which skill fits? Invoke `ask-matt` — it interviews you briefly and routes you to the right skill.

# Built-in Skills

The `superpowers` npm package ships 14 built-in skills covering the most common development workflows.

**Location:** `%USERPROFILE%\.config\opencode\node_modules\superpowers\skills\`

## Skills list

| Skill | Purpose |
|-------|---------|
| `brainstorming` | Explore requirements and design before writing code |
| `systematic-debugging` | Structured diagnosis loop for bugs and regressions |
| `test-driven-development` | Red-green-refactor workflow |
| `writing-plans` | Write detailed implementation plans |
| `executing-plans` | Execute a plan task-by-task with checkpoints |
| `subagent-driven-development` | Dispatch parallel subagents per task |
| `dispatching-parallel-agents` | Run independent tasks in parallel |
| `using-git-worktrees` | Isolated workspace via git worktrees |
| `finishing-a-development-branch` | Integrate completed work |
| `receiving-code-review` | Process review feedback rigorously |
| `requesting-code-review` | Self-review before merging |
| `verification-before-completion` | Run verification before claiming done |
| `using-superpowers` | Meta-skill: how to find and use all skills |
| `writing-skills` | Create new skill files |
| `writing-plans` | Implementation planning |

## Invoking a skill

```
skill brainstorming
```

Or reference it by full name in conversation:

```
use the brainstorming skill to design this feature
```

!!! tip "using-superpowers"
    The `using-superpowers` skill is the master router. It tells OpenCode when and how to invoke all other skills automatically. It is loaded as part of the system prompt when the superpowers plugin is active.

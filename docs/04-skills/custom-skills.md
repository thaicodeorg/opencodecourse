# Custom Skills

You can write your own skills for any workflow you repeat regularly.

## Skill file structure

A skill is a directory containing a `SKILL.md` file:

```
~/.agents/skills/my-skill/
└── SKILL.md
```

## Minimal SKILL.md

```markdown
# Skill: my-skill

## Purpose
One sentence describing what this skill does.

## When to use
Trigger conditions — when should OpenCode invoke this?

## Steps
1. Step one
2. Step two
3. Step three
```

## A real example — `code-review`

```markdown
# Skill: code-review

Review changes since a fixed point along two axes:
- Standards: does the code follow this repo's conventions?
- Spec: does the code match what the issue asked for?

## Steps
1. Identify the base commit/branch
2. Run standards review as subagent
3. Run spec review as subagent
4. Present both reviews side by side
```

## Registering your skill

Place it in `%USERPROFILE%\.agents\skills\<name>\SKILL.md`. OpenCode discovers it automatically — no config change needed.

## Tips for good skills

- **One clear purpose** — skills that try to do everything do nothing well
- **Explicit trigger conditions** — when should this skill fire?
- **Numbered steps** — agents follow ordered steps reliably
- **No ambiguity** — write for an agent with no context, not a human colleague

!!! tip "Use the writing-skills skill"
    OpenCode ships a `writing-skills` skill that guides you through creating well-formed skill files. Invoke it with `skill writing-skills`.

# GitCat for Claude Code

GitCat is a reusable Claude Code skill for code review, repository understanding, architecture mapping, bug investigation, and evidence-based repository health assessments.

## Install in one project

Copy the `gitcat` directory into your project's `.claude/skills/` directory:

```bash
mkdir -p .claude/skills
cp -R gitcat .claude/skills/gitcat
```

The result should be:

```text
your-project/
└── .claude/
    └── skills/
        └── gitcat/
            ├── SKILL.md
            ├── LICENSE.txt
            └── references/
                └── review-checklist.md
```

Run Claude Code from that project and invoke `/gitcat`.

## Install for your user account

Copy the `gitcat` directory to `~/.claude/skills/gitcat`:

```bash
mkdir -p ~/.claude/skills
cp -R gitcat ~/.claude/skills/gitcat
```

This makes it available across your local projects.

## Examples

```text
/gitcat review
/gitcat review src/
/gitcat explain src/services/auth.ts
/gitcat architecture
/gitcat health
/gitcat bug checkout fails when coupon is empty
/gitcat fix handle API timeouts safely
```

## Design principles

- Reviews are read-only unless you explicitly ask for changes.
- Findings should cite real file locations and concrete failure modes.
- Tests are reported as run only when actually executed.
- No destructive Git operations, commits, pushes, or deployments without explicit authorization.
- Health assessments are evidence-based; no invented coverage or quality metrics.

## Customize

Edit `gitcat/SKILL.md` to add your preferred review format, supported stacks, or team-specific conventions. Keep tool/framework claims aligned with what the skill actually does.

## License

GitCat is licensed under the Apache License 2.0. See [LICENSE.txt](LICENSE.txt).

# GitCat for Claude Code and Kilo Code

GitCat is a reusable Agent Skill for code review, repository understanding, architecture mapping, bug investigation, and evidence-based repository health assessments. It follows the portable Agent Skills `SKILL.md` format and can be used by Claude Code, Kilo Code, and compatible agents.

## Install in Kilo Code (Windows, global)

From a PowerShell window, clone the repository if you have not already:

```powershell
cd $HOME\Downloads
git clone https://github.com/adamfutur/gitcat-skills.git
```

Then install GitCat into Kilo Code's global skills directory:

```powershell
New-Item -ItemType Directory -Force "$HOME\.kilo\skills" | Out-Null
Copy-Item -Recurse "$HOME\Downloads\gitcat-skills\skills\gitcat" "$HOME\.kilo\skills\gitcat"
```

For Kilo Code versions configured to use the legacy directory, use `$HOME\.kilocode\skills\gitcat` instead of `$HOME\.kilo\skills\gitcat`.

## Install in Kilo Code (one project)

From your project root, run:

```powershell
New-Item -ItemType Directory -Force ".kilo\skills" | Out-Null
Copy-Item -Recurse "$HOME\Downloads\gitcat-skills\skills\gitcat" ".kilo\skills\gitcat"
```

Kilo Code also supports compatible skill locations such as `.claude/skills/` and `.agents/skills/`. For the current recommended Kilo Code project-level location, use `.kilo/skills/gitcat/SKILL.md`.

After installing, start a new Kilo Code session or run `/reload` to rediscover skills. Then invoke `/gitcat` or ask Kilo Code to use the GitCat skill for a review, explanation, architecture map, repository health assessment, bug investigation, or fix.

## Install in Claude Code

Copy the `gitcat` directory into your project's `.claude/skills/` directory:

```bash
mkdir -p .claude/skills
cp -R skills/gitcat .claude/skills/gitcat
```

For a user-wide installation:

```bash
mkdir -p ~/.claude/skills
cp -R skills/gitcat ~/.claude/skills/gitcat
```

## Expected structure

```text
gitcat/
├── SKILL.md
├── LICENSE.txt
├── README.md
└── references/
    └── review-checklist.md
```

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

Edit `SKILL.md` to add your preferred review format, supported stacks, or team-specific conventions. Keep tool/framework claims aligned with what the skill actually does.

## License

GitCat is licensed under the Apache License 2.0. See [LICENSE.txt](LICENSE.txt).

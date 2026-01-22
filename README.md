# Claude Code Skills & Commands

Personal repository for Claude Code custom skills and commands.

## Structure

```
├── commands/          # Slash commands (simpler, single-file)
│   ├── push.md        # /push - auto-commit and push to GitHub
│   ├── dev.md         # /dev - start Netlify dev server
│   └── wrap.md        # /wrap - wrap up session
├── design/            # Design skill with supporting assets
│   ├── SKILL.md       # Main skill definition
│   ├── DESIGN_MASTER.md
│   ├── assets/
│   └── references/
```

## Installation

Skills and commands are symlinked into Claude's config directory:

```bash
# Commands go in ~/.claude/commands/
ln -sf /home/marc/DEV/claude/commands/push.md ~/.claude/commands/push.md

# Skills go in ~/.claude/skills/
ln -sf /home/marc/DEV/claude/design/SKILL.md ~/.claude/skills/design.md
```

## Adding New Commands

1. Create `commands/my-command.md` with frontmatter:
   ```yaml
   ---
   description: Short description
   allowed-tools: Bash(git:*), Read, Edit
   ---
   ```
2. Add instructions in markdown
3. Symlink: `ln -sf ~/DEV/claude/commands/my-command.md ~/.claude/commands/`
4. Use with `/my-command`

## Adding New Skills

1. Create directory `skills/my-skill/` or add to existing structure
2. Add `SKILL.md` with frontmatter:
   ```yaml
   ---
   name: my-skill
   description: What this skill does and when to use it
   ---
   ```
3. Symlink: `ln -sf ~/DEV/claude/skills/my-skill/SKILL.md ~/.claude/skills/my-skill.md`

## Current Skills

| Name | Description |
|------|-------------|
| design | Frontend design guidance - typography, colors, animations, avoiding generic aesthetics |

## Current Commands

| Command | Description |
|---------|-------------|
| /push | Auto-commit and push to correct GitHub remote |
| /dev | Kill dev ports and start fresh Netlify dev |
| /wrap | Wrap up session |

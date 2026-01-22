---
description: Push to GitHub
allowed-tools: Bash(git:*)
---

# Push to GitHub

Auto-commit and push all changes to the correct GitHub repository with an AI-generated commit message.

## Step 1: Verify Target Remote (CRITICAL)

Before doing anything else, determine WHERE we will push:

1. Run `git remote -v` to see all configured remotes
2. Run `git rev-parse --abbrev-ref HEAD` to get current branch (if "HEAD", we're detached - STOP and warn user)
3. Run `git config --get branch.<branch-name>.remote` to find which remote this branch tracks
4. Run `git remote get-url <remote-name>` to get the actual URL

### Decision Logic:
- **Single remote + branch tracks it**: Auto-proceed, just show "Pushing to <url>..."
- **Ambiguous situation**: ASK user before pushing

### Edge Case Handling:
- **Detached HEAD**: STOP. Tell user to checkout a branch first.
- **No remotes**: STOP. Tell user to add a remote first.
- **Multiple remotes + no upstream**: ASK user which remote to use. Don't assume.
- **Single remote + no upstream**: Safe to use that remote, set upstream automatically.
- **Branch tracks a remote**: Use that remote, no confirmation needed.

## Step 2: Check for Changes

1. Run `git status` to see current changes (never use -uall flag)
2. Run `git diff` to review staged and unstaged changes
3. If no changes, inform user and stop

## Step 3: Analyze and Commit

1. Run `git log --oneline -5` to see recent commit style
2. Stage all changes with `git add -A`
3. Generate a concise, meaningful commit message matching repo style
4. Create commit with:
   - Generated message
   - Co-Authored-By: Claude <noreply@anthropic.com>

## Step 4: Push

1. Push to the confirmed remote: `git push <remote> <branch>`
2. If no upstream, set it: `git push -u <remote> <branch>`
3. Show success message with the remote URL that was pushed to

## Important
- Auto-push when unambiguous (single remote or branch has upstream)
- ASK user when ambiguous (multiple remotes + no upstream)
- NEVER assume `origin` when multiple remotes exist
- NEVER force push
- Always show which URL was pushed to in the success message

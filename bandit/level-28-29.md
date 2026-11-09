# Bandit Level 28 → 29

**Topic:** Secrets that live on in Git history

## Goal

Clone the bandit28-git repository (same setup as level 27). The README has a credentials section, but the password in it has been blanked out. Find the real one.

## Commands used

```bash
cd "$(mktemp -d)"
git clone ssh://bandit28-git@localhost:2220/home/bandit28-git/repo
cd repo
cat README.md          # password is hidden
git log                # one commit message mentions fixing an info leak
git show <commit-id>   # the diff shows the line that was removed
```

Password for bandit29: `y8Yd2ssKcpHpud7UvOSOxwamRMzIGIeQ`

## What I learned

- **Removing a secret in a new commit doesn't remove it from the repository.** Every old version is still in the history, and `git log` plus `git show` bring it straight back.
- `git log` lists commits with their IDs and messages. `git show <id>` shows what that commit changed, as a diff.
- Commit messages are a useful clue. A message about fixing a leak tells you exactly where the leak was.
- Cleaning a secret out properly means rewriting history (for example with `git filter-repo`) _and_ changing the secret, because anyone who already cloned the repo still has it.

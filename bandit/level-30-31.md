# Bandit Level 30 → 31

**Topic:** Git tags

## Goal

Clone the bandit30-git repository. The README has nothing useful, and neither the history nor the branches give anything away. The password is stored somewhere else in the repository.

## Commands used

```bash
cd "$(mktemp -d)"
git clone ssh://bandit30-git@localhost:2220/home/bandit30-git/repo
cd repo
git tag                # lists tags; there's one that isn't a version number
git show <tag-name>    # shows what the tag points to
```

Password for bandit31: `jq9Dfg2rXsfYsWMgFuKlXhphjdH7USgX`

## What I learned

- **Tags are named pointers into a repository**, usually used to mark releases (`v1.0`). They show up in `git tag`, not in `git log` or `git branch`.
- A tag doesn't have to point to a commit. It can point straight to a file's contents (a blob), which is how data can sit in a repo without appearing in any branch.
- `git show <tag>` prints whatever the tag refers to.
- After 28 and 29, the pattern is clear: when the working files don't have the answer, check every other place Git stores things (history, branches, tags).

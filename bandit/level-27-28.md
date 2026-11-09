# Bandit Level 27 → 28

**Topic:** Cloning a Git repository over SSH

## Goal

There's a Git repository on the server at `ssh://bandit27-git@localhost/home/bandit27-git/repo`, port 2220. The `bandit27-git` user has the same password as bandit27. Clone it and find the next password inside.

## Commands used

```bash
cd "$(mktemp -d)"     # home directory isn't writable
git clone ssh://bandit27-git@localhost:2220/home/bandit27-git/repo
# enter bandit27's password when asked
cd repo
ls
cat README
```

Password for bandit28: `STJLJBRRphMxKB392CT4iOr5CbzPU9ER`

## What I learned

- **Git can clone over SSH**, not just HTTPS. The URL format is `ssh://user@host:port/path/to/repo`, and authentication uses the normal SSH login for that user.
- `git clone` copies the whole repository, including its full history. That becomes important in the next few levels.
- This level is the first in a set of five Git levels (27–31), each built around a different Git feature.

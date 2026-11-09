# Bandit Level 31 → 32

**Topic:** Pushing to a remote, and `.gitignore`

## Goal

Clone the bandit31-git repository. This time the README gives a task instead of a password: create a file with specific content and **push** it to the remote's master branch. The server checks the push and replies with the next password.

## Commands used

> _I didn't record my exact commands for this level. These are the steps the task needs; check them against what you ran._

```bash
cd "$(mktemp -d)"
git clone ssh://bandit31-git@localhost:2220/home/bandit31-git/repo
cd repo
cat README.md                       # describes the file to create
# create the file with the content the README asks for
git add -f <file>                   # -f because .gitignore excludes it
git commit -m "<message>"
git push origin master              # the server's reply includes the password
```

Password for bandit32: `82NkymblpGBYmIXG6ZQ8YldBYstHpfUf`

## What I learned

- **`.gitignore`** lists files Git should skip. A plain `git add` silently ignores a matching file, and `git add -f` forces it in.
- `git push` sends local commits to the remote. Server-side hooks can run on a push and print messages back, which is how this level returns the password even though the push itself is rejected.
- This level is the reverse of 27–30: instead of reading from a repo, I had to write to one.

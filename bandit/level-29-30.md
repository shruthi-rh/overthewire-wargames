# Bandit Level 29 → 30

**Topic:** Git branches

## Goal

Clone the bandit29-git repository. The README on the default branch says there are no passwords in production. Find the version of the README that does have one.

## Commands used

```bash
cd "$(mktemp -d)"
git clone ssh://bandit29-git@localhost:2220/home/bandit29-git/repo
cd repo
ls -la
cat README.md          # no password on this branch
git log                # nothing useful in this branch's history
git branch             # only shows the local branch
git branch -a          # also shows remote branches, including a dev branch
git checkout dev
ls
cat README.md
```

Password for bandit30: `Em7eGtqaMySwNFjCpwzzHhLhospOcdt0`

## What I learned

- **A repository can have several branches with different content.** Cloning checks out only the default one, so files on other branches don't show up in `ls`.
- `git branch` lists local branches only. `git branch -a` includes the remote-tracking branches (`remotes/origin/...`) that came with the clone.
- `git checkout <branch>` switches to another branch, and the working directory changes to match it.
- The hint "no passwords in production" pointed to a non-production branch, such as dev.

## Dead ends

- Checking `git log` on the default branch first. The password wasn't in that branch's history at all.
- `git branch` on its own only showed one branch. I needed `-a` to see the rest.

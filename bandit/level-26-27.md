# Bandit Level 26 → 27

**Topic:** Using a setuid helper once you have a shell

## Goal

Now that I can get a real shell as bandit26 (the same `more` → `vi` → `:shell` escape as level 25), I need to read bandit27's password.

## Commands used

```bash
# Get a shell as bandit26 the same way as level 25 (small terminal, v, :set shell=/bin/bash, :shell)

ls -l                                         # shows the bandit27-do binary with the setuid bit
./bandit27-do cat /etc/bandit_pass/bandit27
```

Password for bandit27: ` jHdv2ELQhT22BkprMNDjybZDAkw1zeBJ`

## What I learned

- This is the same idea as level 19: a **setuid binary** runs with its owner's permissions, not the caller's. `bandit27-do` is owned by bandit27, so any command passed to it can read bandit27's files.
- `ls -l` is the quickest way to spot this: an `s` in place of the owner's `x` (`-rwsr-x---`) means setuid.
- The hard part of this level was really level 25's escape. Once I had a shell, the rest used a pattern I already knew.

# Bandit Level 6 → 7

**Topic:** Searching the whole filesystem by owner and group, and hiding errors

## Goal

The password is stored _somewhere on the server_ in a file that is owned by user `bandit7`, owned by group `bandit6`, and 33 bytes in size.

## Commands used

```bash
find / -type f -size 33c -user bandit7 -group bandit6
cat <path-found-above>
```

Password for bandit7: `Bmnnvf82KzQlfxgAI2d1zYbr1u9pr3E3`

## What I learned

- `find /` searches from the root of the filesystem, so the search covers everything.
- `-user` and `-group` filter on ownership, which ties into how Linux permissions work (owner / group / others).

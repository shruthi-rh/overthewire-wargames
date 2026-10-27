# Bandit Level 6 → 7

**Topic:** Searching the whole filesystem by owner and group, and hiding errors

## Goal

The password is stored *somewhere on the server* in a file that is owned by user `bandit7`, owned by group `bandit6`, and 33 bytes in size.

## Commands used

```bash
find / -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null
cat <path-found-above>
```

Password for bandit7: `[redacted]`

## What I learned

- `find /` searches from the root of the filesystem, so the search covers everything.
- `-user` and `-group` filter on ownership, which ties into how Linux permissions work (owner / group / others).
- **Redirection:** `2>/dev/null` sends stderr (file descriptor 2) to `/dev/null`, which discards it. Normal results (stdout, fd 1) still show.

## Dead ends

- My first run without `2>/dev/null` buried the one useful line under hundreds of `Permission denied` errors, because bandit6 can't read most of the filesystem. I had to scroll back to find it.

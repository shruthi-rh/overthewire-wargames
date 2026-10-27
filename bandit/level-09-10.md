# Bandit Level 9 → 10

**Topic:** Pulling readable text out of binary data with `strings`

## Goal

`data.txt` is mostly binary. The password is one of the few human-readable strings, and it comes right after several `=` characters.

## Commands used

```bash
strings data.txt | grep "="
```

Password for bandit10: `[redacted]`

## What I learned

- `strings` scans any file and prints runs of printable characters (4+ by default). It's a first step for looking inside binaries.
- Combined with `grep`, it finds the needle quickly.

## Dead ends

- `grep "=" data.txt` → `binary file matches` and no output. `grep` refuses to print binary content (`grep -a` forces it, but the output is messy).
- I first typed `strings data.txt grep "="`, without the pipe. `strings` then treated `grep` and `=` as extra filenames to open, and the output wasn't filtered.

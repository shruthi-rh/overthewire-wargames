# Bandit Level 5 → 6

**Topic:** `find` with size and permission filters

## Goal

Somewhere under `inhere` (many subdirectories) is a file that is human-readable, exactly 1033 bytes, and not executable. Find it.

## Commands used

```bash
cd inhere
find . -type f -size 1033c ! -executable -exec file {} + | grep ASCII
```

Password for bandit6: `[redacted]`

## What I learned

- `find` can filter on almost any file property:
  - `-type f`: regular files only
  - `-size 1033c`: exactly 1033 **bytes**. The `c` suffix matters: without it, `find` counts in 512-byte blocks.
  - `! -executable` (or `-not -executable`): negates a test
- Chaining tests narrows a huge directory tree down to one result, and `-exec file {} +` confirms that it's text.

## Dead ends

- `-size 1033` without `c` returned nothing, because it was searching in 512-byte blocks.
- Browsing the 20 `maybehereXX` directories by hand would have taken ages. This level is designed to push you towards `find`.

# Bandit Level 8 → 9

**Topic:** `sort` + `uniq` to find the one unique line

## Goal

In `data.txt`, every line is repeated several times except one. That unique line is the password.

## Commands used

```bash
sort data.txt | uniq -u
```

Password for bandit9: `EjmOSvuAu7sGAHqHVcBDPirRe9T03kxl`

## What I learned

- `uniq` only compares **adjacent** lines, so the input has to be sorted first for duplicates to sit next to each other.
- `uniq -u` prints only lines that appear once. `uniq -c` prefixes counts, and `sort | uniq -c | sort -n` is a handy frequency count.

## Dead ends

- `uniq -u data.txt` without sorting printed almost the whole file, because the duplicates weren't next to each other.

# Bandit Level 7 → 8

**Topic:** `grep` for a keyword

## Goal

`data.txt` is a large file of word/password pairs. The password is on the line next to the word `millionth`.

## Commands used

```bash
grep "millionth" data.txt
```

Password for bandit8: `[redacted]`

## What I learned

- `grep PATTERN FILE` prints only the lines that match. It's the fastest way to pull one line out of a huge file.
- Useful flags I noted for later: `-i` (ignore case), `-n` (line numbers), `-v` (invert), `-r` (recursive), `-c` (count).

## Dead ends

- `cat data.txt` scrolled thousands of lines past, which isn't useful.
- Curly quotes (`“millionth”`) copied from my notes again. In this case `grep` searched for the quote characters as part of the pattern and found nothing.

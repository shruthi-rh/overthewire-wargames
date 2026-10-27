# Bandit Level 1 → 2

**Topic:** Files whose name is `-`

## Goal

The password is in a file literally named `-` in the home directory.

## Commands used

```bash
ls
cat ./-
```

Password for bandit2: `[redacted]`

## What I learned

- Many programs treat `-` as shorthand for **stdin** (standard input) instead of a filename. `cat -` waits for you to type something instead of opening the file.
- Prefixing the name with a path (`./-`) makes it unambiguous: `./` means "in the current directory", so the shell passes it through as a real filename.
- `cat < -` also works, because then the shell opens the file and feeds it in through redirection.

## Dead ends

- `cat -` just hung. It was waiting for keyboard input, not stuck. `Ctrl+C` gets you out.

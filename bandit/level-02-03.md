# Bandit Level 2 → 3

**Topic:** Spaces and leading dashes in filenames

## Goal

The password is in a file called `--spaces in this filename--`. The name causes two problems at once: spaces, and leading dashes.

## Commands used

```bash
ls
cat -- "--spaces in this filename--"
# or
cat ./"--spaces in this filename--"
```

Password for bandit3: `[redacted]`

## What I learned

- **Spaces:** the shell splits arguments on spaces, so the name has to be quoted (or each space escaped with `\ `).
- **Leading dashes:** even with quotes, `cat` sees `--spaces...` and tries to parse it as an option. `--` is the standard "end of options" marker. Everything after it is treated as a filename.
- `./` works here too, the same trick as level 1.
- Tab completion handles the escaping for you: type `cat ./--sp` and press Tab.

## Dead ends

- `cat --spaces in this filename--` → `cat` complained about an unrecognized option, then treated `in`, `this`, and so on as separate files.
- Quoting alone (`cat "--spaces in this filename--"`) still fails, because quotes fix the spaces but not the dashes.
- **Copying commands from my notes broke them.** My notes app auto-converted `--` into an em-dash (`—`) and straight quotes into curly quotes (`“ ”`). The shell doesn't recognize either. Since then I keep commands in a plain-text/Markdown file (this repo).

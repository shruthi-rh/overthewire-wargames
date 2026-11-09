# Bandit Level 4 → 5

**Topic:** Identifying file types

## Goal

The `inhere` directory has several files named `-file00` to `-file09`. Only one is human-readable, and that one holds the password.

## Commands used

```bash
cd inhere
file ./*
find . -type f -exec file {} + | grep "text"
```

Password for bandit5: `6C7h9GD8M6ai5nr7wo1RonrzFjj9yIrG `

## What I learned

- `file` inspects a file's contents (its "magic bytes") to say what it actually is, such as `ASCII text` or `data`, no matter what the name or extension says.
- `find . -type f -exec file {} +` runs `file` on every regular file under the current directory. `{}` is replaced by the filenames, and `+` batches them into one call instead of one call per file (`\;`).
- Piping the result into `grep "text"` leaves only the readable file.
- Same leading-dash problem as before: `file *` breaks because the names start with `-`, so `./*` is safer.

## Dead ends

- `cat`-ing each file one by one. The binary ones dump garbage into the terminal and can even mess up its display (`reset` fixes it). I initially tried this and eventually landed at the result ultimately, but this isn't the best way to do it. So, after a couple of google searches later, I learned how to use the different flags that the file command had to offer as well as how to pipe its output to grep.
- `file *` → the `-file0X` names were parsed as options.

# Bandit Level 4 → 5

**Topic:** Identifying file types

## Goal

The `inhere` directory has several files named `-file00` to `-file09`. Only one is human-readable, and that one holds the password.

## Commands used

```bash
cd inhere
file ./*
# more generally, recursive:
find . -type f -exec file {} + | grep "text"
```

Password for bandit5: `[redacted]`

## What I learned

- `file` inspects a file's contents (its "magic bytes") to say what it actually is, such as `ASCII text` or `data`, no matter what the name or extension says.
- `find . -type f -exec file {} +` runs `file` on every regular file under the current directory. `{}` is replaced by the filenames, and `+` batches them into one call instead of one call per file (`\;`).
- Piping the result into `grep "text"` leaves only the readable file.
- Same leading-dash problem as before: `file *` breaks because the names start with `-`, so `./*` is safer.

## Dead ends

- `cat`-ing each file one by one. The binary ones dump garbage into the terminal and can even mess up its display (`reset` fixes it).
- `file *` → the `-file0X` names were parsed as options.

# Bandit Level 3 → 4

**Topic:** Hidden files

## Goal

The password is in a hidden file inside the `inhere` directory.

## Commands used

```bash
cd inhere
ls          # shows nothing
ls -la      # shows the hidden file
cat ./<hidden-file-name>
```

Password for bandit4: `[redacted]`

## What I learned

- On Linux, any file whose name starts with `.` is **hidden** from a plain `ls`. It's a naming convention, not a security feature.
- `ls -a` shows all entries, including `.` (current dir) and `..` (parent dir). `ls -l` adds permissions, owner, size, and date. `ls -la` combines both, and I use it by default now.

## Dead ends

- A plain `ls inhere` returned nothing, which made the directory look empty.

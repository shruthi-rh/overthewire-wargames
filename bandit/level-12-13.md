# Bandit Level 12 → 13

**Topic:** Reversing a hexdump, then peeling off layers of compression

## Goal

`data.txt` is a hexdump of a file that has been compressed many times over with different tools. Turn it back into binary, then decompress layer by layer until plain text appears.

## Commands used

```bash
# Work in a scratch directory: the home dir isn't writable
cd "$(mktemp -d)"
cp ~/data.txt .

xxd -r data.txt > data          # hexdump -> original binary
file data                        # tells you which compressor was used

# Then repeat: check with `file`, rename to the right extension, decompress
mv data data.gz && gzip -d data.gz
mv data data.bz2 && bzip2 -d data.bz2
tar -xf data                     # for "POSIX tar archive"
file <whatever-came-out>
# ...loop until `file` says "ASCII text"
cat <final-file>
```

Password for bandit13: `[redacted]`

## What I learned

- **`xxd -r`** reverses a hexdump back into the original bytes.
- **`file` is the guide for the whole level.** You don't need to guess. Every step is "run `file`, use the matching tool".
- Which tool goes with which `file` output:
  - `gzip compressed data` → `gzip -d` (expects a `.gz` extension)
  - `bzip2 compressed data` → `bzip2 -d`
  - `POSIX tar archive` → `tar -xf`
- `mktemp -d` creates a unique writable temp directory, the usual way to get scratch space on a shared server.

## Dead ends

- Running `xxd -r` in the home directory → `Permission denied`. That's why I needed `mktemp -d`.
- `gzip -d data` failed with `unknown suffix -- ignored`. gzip needs a `.gz` extension, so I had to rename the file first.
- I lost track of which file was the newest a couple of times. `ls -lt` (sort by time) helped.
- This was the longest level so far, purely from the number of layers. Being methodical (`file` → decompress → `file` again) mattered more than knowing anything clever.

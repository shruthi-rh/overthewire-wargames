# Bandit Level 10 → 11

**Topic:** Base64 decoding

## Goal

`data.txt` contains base64-encoded data. Decode it to get the password.

## Commands used

```bash
cat data.txt          # looks like random letters/digits ending in "="
base64 -d data.txt
```

Password for bandit11: `[redacted]`

## What I learned

- **Base64 is an encoding, not encryption.** It represents binary data with 64 printable characters (`A–Z a–z 0–9 + /`) so it can travel safely through text-only channels. Anyone can reverse it, and no key is involved.
- How to recognise it: only those characters, a length that's a multiple of 4, often ending in `=` or `==` padding.
- `base64` encodes, `base64 -d` decodes.

## Dead ends

- None that cost much time. The trailing `=` gave it away as base64. The useful lesson was recognising the format by sight.

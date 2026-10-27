# Bandit Level 11 → 12

**Topic:** ROT13 with `tr`

## Goal

`data.txt` contains text where every letter has been rotated by 13 positions (ROT13). Undo the rotation.

## Commands used

```bash
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```

Password for bandit12: `[redacted]`

## What I learned

- **ROT13** is a Caesar cipher with a shift of 13. Since the alphabet has 26 letters, applying it twice gives back the original, so the same command both encodes and decodes.
- `tr SET1 SET2` translates characters one-to-one. `A-Z` → `N-ZA-M` maps A→N, B→O, …, M→Z, N→A, …, Z→M. Lowercase works the same way.
- Like base64, this is obfuscation with no secret involved, not real encryption.

## Dead ends

- My first attempt only mapped uppercase (`tr 'A-Z' 'N-ZA-M'`), so the lowercase letters stayed scrambled.

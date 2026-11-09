# Bandit Level 17 → 18

**Topic:** Comparing two files with `diff`

## Goal

The home directory has two files, `passwords.old` and `passwords.new`. The password for the next level is the **only line that was changed** between them.

(This level is reached by logging in with the SSH private key from level 16, not a password.)

## Commands used

What I know so far:

- `diff` compares two files line by line and shows what differs.
- The output marks lines from the first file with `<` and lines from the second with `>`. The next password is on the `new` side, so I need to be careful about which one I pick.

Password for bandit18: `OQxXZjELndr90zuhOTDYBEomI0SZITXI`

## What I learned

- How to read `diff` output (`<` vs `>`, the change markers like `3c3`)
- Other ways to compare files (`comm`, `sdiff`, `diff -u`)
- Why argument order matters when running `diff`

## Dead ends

- Nothing in specific

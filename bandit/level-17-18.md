# Bandit Level 17 → 18

**Topic:** Comparing two files with `diff`

> 🔄 **In progress.** I'll fill in the commands and dead ends once I've solved it.

## Goal

The home directory has two files, `passwords.old` and `passwords.new`. The password for the next level is the **only line that was changed** between them.

(This level is reached by logging in with the SSH private key from level 16, not a password.)

## Commands used

_To be completed._

What I know so far:

- `diff` compares two files line by line and shows what differs.
- The output marks lines from the first file with `<` and lines from the second with `>`. The next password is on the `new` side, so I need to be careful about which one I pick.

Password for bandit18: `[redacted]`

## What I learned

_To be completed._ Topics to read up on:

- How to read `diff` output (`<` vs `>`, the change markers like `3c3`)
- Other ways to compare files (`comm`, `sdiff`, `diff -u`)
- Why argument order matters when running `diff`

## Dead ends

_To be completed._

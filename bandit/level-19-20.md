# Bandit Level 19 → 20

**Topic:** Setuid binaries and running commands as another user

## Goal

To get the password for the next level, I need to use the **setuid binary** in the home directory. Running it executes a command I give it as the user `bandit20`, and as bandit20 I can read that user's password file.

## Commands used

What I know so far:

- Run the binary with no arguments first to see how it expects to be used.
- Passwords for each level live in `/etc/bandit_pass/`, readable only by the matching user.
- `ls -l` on the binary shows an `s` in the permission bits. That is the setuid flag.

Password for bandit20: `4pIjcunZ0fK2vmp3IwfG8Vf7VhxD6pOA`

## What I learned

Topics to read up on:

- What the setuid bit does (real UID vs effective UID)
- Why setuid programs are a common privilege-escalation target
- File permissions on `/etc/bandit_pass/*` and why they work as access control here

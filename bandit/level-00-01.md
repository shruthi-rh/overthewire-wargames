# Bandit Level 0 → 1

**Topic:** SSH login, listing and reading files

## Goal

Log in to the game server over SSH as `bandit0` (the password is given on the level page), then find the password for the next level. It's in a file called `readme` in the home directory.

## Commands used

```bash
ssh -p 2220 bandit0@bandit.labs.overthewire.org
ls
cat readme
```

Password for bandit1: `[redacted]`

## What I learned

- **SSH basics:** `ssh user@host` opens a remote shell. The server doesn't listen on the default port 22, so `-p 2220` is needed to pick the port.
- `ls` lists a directory's contents and `cat` prints a file to the terminal.
- The structure of the whole game: each level's password is how you log in as the next user, so every level ends with `ssh -p 2220 bandit<N+1>@...`.

## Dead ends

- At first I treated level 0 as only "connect to the server". The actual task for 0 → 1 is reading the file once you're in.
- If you leave out `-p 2220`, SSH tries port 22 and the connection just hangs or gets refused. The port flag is easy to forget.

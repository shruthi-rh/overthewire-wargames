# Bandit Level 18 → 19

**Topic:** Running a command over SSH when the login shell is sabotaged

## Goal

The password is stored in a file called `readme` in the home directory. The catch: someone modified `.bashrc` so that **logging in over SSH immediately logs you out**. I need to read the file anyway.

## Commands used

What I know so far:

- The logout happens because `.bashrc` runs when an interactive shell starts.
- `ssh` can run a single command on the remote host instead of opening an interactive shell, which is the way around this.
- Other things worth trying: `ssh -T` (no pseudo-terminal), or `ssh -t` with a different shell.

Password for bandit19: `KpsOfPkcP7i1FlIExk2QEjyt6dw8dxZI`

## What I learned

- Interactive vs non-interactive shells, and which startup files each one reads (`.bashrc`, `.profile`, `.bash_profile`)
- How `ssh user@host <command>` differs from a normal login
- What a pseudo-terminal (`-t` / `-T`) actually is

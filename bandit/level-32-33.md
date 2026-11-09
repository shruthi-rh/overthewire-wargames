# Bandit Level 32 → 33

**Topic:** Escaping a shell that uppercases everything

## Goal

Logging in as bandit32 drops me into an "uppercase shell": every command I type is converted to uppercase before it runs. Linux commands are lowercase (`ls`, `cat`), so nothing works. I need a normal shell to read the next password.

## Commands used

> _Add the command you used to get out of the uppercase shell._

```bash
# once out of the uppercase shell:
ls -la                          # the uppercase shell binary is setuid bandit33
whoami                          # confirms I'm running as bandit33
cat /etc/bandit_pass/bandit33
```

Password for bandit33: `pWuj5jBQ6IgV0NXwiH6g1pXRF8S1YvbT`

## What I learned

- **A shell filter only works on what it can change.** Uppercasing breaks letters, but anything with no letters in it (symbols, digits, shell variables like `$0`) gets through unchanged.
- `ls -la` showed the uppercase shell is a setuid program owned by bandit33. Any shell it starts runs as bandit33, which `whoami` confirmed.
- `whoami` is a quick way to check which user a shell is actually running as, especially after an escape.
- Same theme as level 25: a restricted shell is only as strong as its weakest way out.

## Dead ends

- Typing normal commands (`ls`, `cat`) → they became `LS`, `CAT` and failed with "command not found".

## The end (for now)

Password found: u4P2CyPOwPGLe94RdD9Uo2FxFwvnFswM

bandit33 is currently the last level of Bandit. That completes the game.

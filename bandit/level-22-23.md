# Bandit Level 22 → 23

**Topic:** A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

## Goal

A cron job is running as user bandit23 and periodically executes a script. The task is to inspect the cron configuration and identify how the script generates and stores the password for the next level.

By examining the cron job and its associated shell script, it became clear that the password was written to a file whose name was generated using an MD5 hash of a fixed string. Reproducing the hash locally revealed the filename, allowing access to the password stored in /tmp.

## Commands used

```bash
- cd /etc/cron.d
- cat cronjob_bandit23

- cat /usr/bin/cronjob_bandit23.sh

- echo I am user bandit23 | md5sum

- cat /tmp/<generated_hash>
```

Password for bandit23: `RYVux2rHEm9tiXHmLFzuR7Vhx6AZQMEz`

## What I learned

- How to investigate cron jobs through files stored in /etc/cron.d/.
- How shell scripts can dynamically generate filenames.
- How MD5 hashing can be used to create predictable file names.
- How to reproduce script behavior manually to discover hidden resources.
- How temporary directories such as /tmp are often used for inter-process communication.
- How command substitution works in shell scripts.
- How to analyze scripts line by line to understand data flow.

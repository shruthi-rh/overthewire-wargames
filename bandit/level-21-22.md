# Bandit Level 21 → 22

**Topic:** A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

## Goal

A program is being executed automatically through a cron job. By inspecting the cron configuration files in /etc/cron.d/, the task was to identify which command was running and determine how it could be exploited to retrieve the password for the next level.

The cron job executed the suconnect program as user bandit22. The program connected to a TCP port specified as an argument and sent the current level's password. By creating a listener with nc (netcat) on a chosen port and then executing suconnect with that port number, I was able to receive the password for bandit22, which is the password required to log in as bandit22 and continue to the next challenge.

## Commands used

```bash
- echo -n 'bW9kBv5WC3P4yoDyf12LSdGuNz5ka6hY' | nc -l -p 1234 &
- ./suconnect 1234
```

Password for bandit22: `bW9kBv5WC3P4yoDyf12LSdGuNz5ka6hY`

## What I learned

- How to inspect cron jobs using files in /etc/cron.d/.
- How automated scheduled tasks can execute programs with different user privileges.
- How to read shell scripts and understand what commands are being executed by cron.
- How TCP client-server communication works at a basic level.
- How to use nc (netcat) to create a listening TCP server.
- How background processes work using the & operator.
- How the suconnect program connected to a specified port and transmitted data.

# Bandit Level 14 → 15

**Topic:** Sending data to a local network port with `nc`

## Goal

Submit the current level's password (bandit14's) to a service listening on **port 30000 on localhost**. If it's correct, the service replies with the next password.

## Commands used

```bash
# Logged in as bandit14
cat /etc/bandit_pass/bandit14 | nc localhost 30000
# or interactively:
nc localhost 30000
# then paste the password and press Enter
```

Password for bandit15: `[redacted]`

## What I learned

- **Ports:** one machine can run many network services, and each listens on its own port number. `localhost` (127.0.0.1) means "this same machine", so the service is only reachable from inside the server.
- **`nc` (netcat)** opens a raw TCP connection. Whatever goes into its stdin is sent over the socket, and the reply is printed. It's a general-purpose tool for poking at network services by hand.
- Piping the password in (`cat file | nc ...`) avoids copy-paste mistakes and sends the trailing newline the service expects.
- Getting the password from `/etc/bandit_pass/bandit14` was a nice payoff from level 13. The previous level explicitly pointed there.

## Dead ends

- I first ran `nc` from my own machine against `bandit.labs.overthewire.org 30000`. It timed out, because the port only listens on localhost on the server. The command has to run on the server.
- Sending the password without a newline (e.g. `echo -n`) → the service waited for more input. Plain `echo` / `cat` include the newline.
- Typing `nc localhost 30000` and then just waiting. Netcat doesn't prompt; it's already connected and waiting for you to send something.

# Bandit Level 13 → 14

**Topic:** Authenticating with an SSH private key

## Goal

There's no password for bandit14 this time. Instead, the home directory has a **private SSH key** (`sshkey.private`) that lets you log in as `bandit14`. Once logged in, the next password can be read from `/etc/bandit_pass/bandit14`.

## Commands used

```bash
# From my own machine: copy the key down from the server
scp -P 2220 bandit13@bandit.labs.overthewire.org:sshkey.private .

# Lock down the key's permissions (Linux/macOS/WSL)
chmod 600 sshkey.private

# Log in as bandit14 with the key instead of a password
ssh -i sshkey.private -p 2220 bandit14@bandit.labs.overthewire.org

# Now on the server as bandit14
cat /etc/bandit_pass/bandit14
```

Password for bandit14: `[redacted]`

## What I learned

- **Public-key authentication:** a key pair is a private key (kept secret, stays with you) and a public key (placed in the server's `~/.ssh/authorized_keys`). The server checks that you hold the matching private key without the key ever being sent. Whoever holds the private key *is* that user, as far as the server is concerned.
- `ssh -i <keyfile>` chooses which private key to use.
- `scp` copies files over SSH. Note it's **`-P`** (uppercase) for the port, unlike `ssh -p`.
- **SSH refuses keys that other users can read.** The key must be readable only by the owner (`600` = `rw-------`).
- `/etc/bandit_pass/banditN` holds each user's password, readable only by that user, which is why you have to *become* bandit14 to read it.

## Dead ends

- `ssh -i sshkey.private bandit14@localhost` from inside the server. Older guides suggest this, but the server now blocks SSH connections to localhost, so I had to copy the key to my own machine.
- `scp -p 2220 ...` with a lowercase `p` → in `scp`, `-p` means "preserve timestamps", so it treated `2220` as a filename. The port flag for scp is `-P`.
- `WARNING: UNPROTECTED PRIVATE KEY FILE!` → SSH ignored the key and asked for a password. The downloaded file was readable by others and needed `chmod 600`.
- **On Windows, `chmod` doesn't fix this.** The OpenSSH client checks Windows file permissions (ACLs), not Unix mode bits. What worked was removing inherited permissions and granting access only to my user:
  ```powershell
  icacls .\sshkey.private /inheritance:r
  icacls .\sshkey.private /grant:r "$($env:USERNAME):(R)"
  ```
  (Running it from WSL, where `chmod 600` behaves normally, also works.)

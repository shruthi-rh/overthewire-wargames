# Bandit Level 16 → 17

**Topic:** Port scanning a range, then finding the one SSL/TLS service that gives credentials back

> 🔄 **In progress.** I'll fill in the commands and dead ends once I've solved it.

## Goal

Submit the current password to a service on localhost, but this time I don't know the port. It's somewhere in the range **31000–32000**. Of the ports in that range, only some have a server listening, only some of those speak **SSL/TLS**, and only one of those hands back the next credentials instead of just echoing my input.

## Commands used

_To be completed._

What I know so far:

- Step 1: scan the range to find open ports (`nmap` is available on the server).
- Step 2: work out which open ports speak SSL/TLS (`nmap -sV` helps with service detection).
- Step 3: connect to the candidates with `openssl s_client` (same as level 15) and send the current password.
- The reply is not a password this time but an **SSH private key** for the next user.
- Save the key to a file in a temp directory (`mktemp -d`) and `chmod 600` it, or SSH will refuse to use it.

Credentials for bandit17: `[redacted]`

## What I learned

_To be completed._ Topics to read up on:

- How `nmap` port ranges and service/version detection work
- Why a server might echo input back instead of answering
- SSH key-based login (`ssh -i`) and why private key permissions matter
- Using `mktemp -d` for a scratch directory on a shared machine

## Dead ends

_To be completed._

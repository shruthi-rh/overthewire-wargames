# Bandit Level 16 → 17

**Topic:** Port scanning a range, then finding the one SSL/TLS service that gives credentials back

## Goal

Submit the current password to a service on localhost, but this time I don't know the port. It's somewhere in the range **31000–32000**. Of the ports in that range, only some have a server listening, only some of those speak **SSL/TLS**, and only one of those hands back the next credentials instead of just echoing my input.

## Commands used

What I know so far:

- Step 1: scan the range to find open ports (`nmap` is available on the server).
- Step 2: work out which open ports speak SSL/TLS (`nmap -sV` helps with service detection).
- Step 3: connect to the candidates with `openssl s_client` (same as level 15) and send the current password.
- The reply is not a password this time but an **SSH private key** for the next user.
- Save the key to a file in a temp directory (`mktemp -d`) and `chmod 600` it, or SSH will refuse to use it.

## What I learned

- How `nmap` port ranges and service/version detection work
- Why a server might echo input back instead of answering
- SSH key-based login (`ssh -i`) and why private key permissions matter
- Using `mktemp -d` for a scratch directory on a shared machine

## Dead ends

- I was stuck on this level longer than any other level, I had some trouble copying the private key from one system to another which led to difficulties logging in. A real headache! Ultimately, I got around it by using scp.

# Bandit Level 15 → 16

**Topic:** Talking to an SSL/TLS service with `openssl s_client`

> 🔄 **In progress.** I'll fill in the commands and dead ends once I've solved it.

## Goal

Same idea as level 14: submit the current password to a service on localhost, this time on **port 30001**. The difference is that this service speaks **SSL/TLS**, so it expects an encrypted connection.

## Commands used

_To be completed._

What I know so far:

- Plain `nc` from level 14 won't work, because netcat sends raw bytes and the server expects a TLS handshake first.
- The level hints point at `openssl s_client` (and `ncat --ssl` as an alternative) for opening an encrypted connection by hand.

Password for bandit16: `[redacted]`

## What I learned

_To be completed._ Topics to read up on:

- What TLS adds on top of TCP (encryption, server certificates)
- What `openssl s_client` prints during the handshake (certificate chain, session details)
- Why the connection might close or behave unexpectedly after sending input

## Dead ends

_To be completed._

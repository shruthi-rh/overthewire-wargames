# Bandit Level 20 → 21

**Topic:** Setuid client binary, running a listener, and job control

## Goal

The home directory has a setuid binary that connects to a port on localhost **that I choose**. It reads a line from that connection and compares it to the current level's password. If it matches, it sends back the next password.

So I have to be the server: set up a listener on a port, feed it the current password, and then run the binary pointed at that port.

## Commands used

What I know so far:

- I need two things running at the same time: a listener (`nc -l`) and the binary connecting to it. That means either two SSH sessions, a background job (`&`), or `tmux`.
- The listener has to send the current password when the binary connects, and then receive the reply.
- Ports below 1024 need root, so pick a high port.

Password for bandit21: `bW9kBv5WC3P4yoDyf12LSdGuNz5ka6hY`

## What I learned

Topics to read up on:

- Client/server roles and how a listener works with `nc -l`
- Shell job control (`&`, `jobs`, `fg`, `bg`)
- Piping or redirecting a value into a listening `nc`
- Using `tmux` or a second SSH session as an alternative to backgrounding

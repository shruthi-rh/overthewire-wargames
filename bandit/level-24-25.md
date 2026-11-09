# Bandit Level 24 → 25

**Topic:** A daemon is listening on port 30002 and will give you the password for bandit25 if given the password for bandit24 and a secret numeric 4-digit pincode. There is no way to retrieve the pincode except by going through all of the 10000 combinations, called brute-forcing. You do not need to create new connections each time

## Goal

A service running on localhost requires the password for the current level followed by a 4-digit PIN. The objective is to discover the correct PIN and obtain the password for the next level.

Since the PIN is only four digits, a brute-force attack is practical. A list containing every possible PIN combined with the current password was generated and sent to the service. The correct combination produced the password for the next level.

## Commands used

```bash
for i in {0000..9999}
do
    echo "gKXDTAXnIz3OBxiPjRZ2uqutUlPZrBsw $i"
done > combinations.txt

cat combinations.txt | nc localhost 30002
```

Password for bandit25: `hVQMk3lJNsmQ7VF3ubyrNNBom7BOgVXv`

## What I learned

- How to interact with network services using nc (netcat).
- How brute-force attacks work against weak authentication mechanisms.
- How to generate large input sets using shell loops.
- How Bash expands numerical ranges.
- How to pipe generated data directly into network services.
- How services respond differently to valid and invalid credentials.
- Why short PINs are vulnerable to brute-force attacks.

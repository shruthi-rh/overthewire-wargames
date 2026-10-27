# Cheatsheet

Commands and concepts I keep coming back to. The levels where each one first came up are in brackets.

## Connecting

| Command | What it does |
|---------|--------------|
| `ssh -p 2220 user@host` | Log in to a remote shell on a non-default port [0] |
| `ssh -i keyfile -p 2220 user@host` | Log in with a private key instead of a password [13] |
| `scp -P 2220 user@host:remote_file .` | Copy a file over SSH. **Capital `-P`** for the port [13] |
| `chmod 600 keyfile` | Make a key readable only by its owner, which SSH requires [13] |
| `icacls key /inheritance:r` + `/grant:r "$env:USERNAME:(R)"` | Windows equivalent of `chmod 600` for SSH keys [13] |

## Looking around

| Command | What it does |
|---------|--------------|
| `ls -la` | List everything, including hidden dotfiles, with permissions/owner/size [3] |
| `file <path>` | Identify what a file really is from its contents [4] |
| `cat ./-` | Read a file named `-` (otherwise treated as stdin) [1] |
| `cat -- "--name with spaces--"` | `--` ends option parsing, and quotes keep spaces together [2] |
| `ls -lt` | Sort by modification time, newest first [12] |

## `find`

```bash
find . -type f                                # regular files under current dir
find . -type f -size 1033c ! -executable      # exact byte size (c = bytes!), not executable  [5]
find / -type f -user bandit7 -group bandit6 2>/dev/null   # by owner/group, hide errors       [6]
find . -type f -exec file {} +                # run `file` on every result (batched)          [4]
```

- `-size N` without a suffix counts **512-byte blocks**. Use `c` for bytes.
- `!` / `-not` negates a test.

## Text processing

| Command | What it does |
|---------|--------------|
| `grep "word" file` | Lines containing `word` [7] |
| `grep -i / -n / -v / -r / -c` | ignore case / line numbers / invert / recursive / count |
| `sort file \| uniq -u` | Lines that appear exactly once. `uniq` needs sorted input [8] |
| `sort \| uniq -c \| sort -n` | Count occurrences of each line |
| `strings file` | Printable text inside a binary file [9] |
| `tr 'A-Za-z' 'N-ZA-Mn-za-m'` | ROT13 encode/decode [11] |

## Encodings and compression

| Seen as | Tool |
|---------|------|
| Base64 (A–Z a–z 0–9 + /, ends in `=`) | `base64 -d` [10] |
| Hexdump | `xxd -r` [12] |
| `gzip compressed data` | `mv f f.gz && gzip -d f.gz` [12] |
| `bzip2 compressed data` | `bzip2 -d f` [12] |
| `POSIX tar archive` | `tar -xf f` [12] |

Encoding ≠ encryption: base64, hex, and ROT13 have no key and anyone can reverse them.

## Shell concepts

- **Pipe** `a | b`: a's output becomes b's input [8]
- **Redirect** `>` (stdout to file), `2>` (stderr), `2>/dev/null` (discard errors) [6]
- `-` often means stdin. `--` means "end of options" [1, 2]
- `mktemp -d`: get a writable scratch directory on a shared machine [12]
- `reset`: fixes a terminal garbled by binary output [4]

## Networking

| Command | What it does |
|---------|--------------|
| `nc host port` | Raw TCP connection: stdin is sent, the reply is printed [14] |
| `cat file \| nc localhost 30000` | Send a file's contents to a local service [14] |
| `openssl s_client -connect host:port` | TLS connection by hand (like `nc` but encrypted) [15] |

- `localhost` / `127.0.0.1` = this machine. A service bound there can't be reached from outside [14].

## Bandit-specific

- `/etc/bandit_pass/banditN`: each user's password, readable only by that user [13, 14]

## Gotchas

- **Never copy commands from a word processor.** It turns `--` into `—` and `"` into `“ ”`, and the shell rejects both.

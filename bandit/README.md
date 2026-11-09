# Bandit

[Bandit](https://overthewire.org/wargames/bandit/) is the beginner wargame. Each level hides the password for the next one somewhere on the server, and finding it means learning a new Linux tool or concept.

Connect with:

```bash
ssh -p 2220 banditN@bandit.labs.overthewire.org
```

## Progress

| Level   | Topic                                         | Status  | Notes                         |
| ------- | --------------------------------------------- | ------- | ----------------------------- |
| 0 → 1   | SSH login, reading a file                     | ✅ Done | [level-00-01](level-00-01.md) |
| 1 → 2   | File named `-`                                | ✅ Done | [level-01-02](level-01-02.md) |
| 2 → 3   | Spaces and dashes in filenames                | ✅ Done | [level-02-03](level-02-03.md) |
| 3 → 4   | Hidden files                                  | ✅ Done | [level-03-04](level-03-04.md) |
| 4 → 5   | Identifying file types                        | ✅ Done | [level-04-05](level-04-05.md) |
| 5 → 6   | `find` with size/permission filters           | ✅ Done | [level-05-06](level-05-06.md) |
| 6 → 7   | Searching the whole filesystem by owner/group | ✅ Done | [level-06-07](level-06-07.md) |
| 7 → 8   | `grep` for a keyword                          | ✅ Done | [level-07-08](level-07-08.md) |
| 8 → 9   | `sort` + `uniq` to find a unique line         | ✅ Done | [level-08-09](level-08-09.md) |
| 9 → 10  | `strings` on binary data                      | ✅ Done | [level-09-10](level-09-10.md) |
| 10 → 11 | Base64 decoding                               | ✅ Done | [level-10-11](level-10-11.md) |
| 11 → 12 | ROT13 with `tr`                               | ✅ Done | [level-11-12](level-11-12.md) |
| 12 → 13 | Hexdump + nested compression                  | ✅ Done | [level-12-13](level-12-13.md) |
| 13 → 14 | SSH private keys                              | ✅ Done | [level-13-14](level-13-14.md) |
| 14 → 15 | Sending data to a local port with `nc`        | ✅ Done | [level-14-15](level-14-15.md) |
| 15 → 16 | SSL/TLS with `openssl s_client`               | ✅ Done | [level-15-16](level-15-16.md) |
| 16 → 17 | Port scanning, finding the right SSL service  | ✅ Done | [level-16-17](level-16-17.md) |
| 17 → 18 | Comparing files with `diff`                   | ✅ Done | [level-17-18](level-17-18.md) |
| 18 → 19 | Running a command over SSH                    | ✅ Done | [level-18-19](level-18-19.md) |
| 19 → 20 | Setuid binaries                               | ✅ Done | [level-19-20](level-19-20.md) |
| 20 → 21 | Setuid client, listener, job control          | ✅ Done | [level-20-21](level-20-21.md) |
| 21 → 22 |                                               | ✅ Done | [level-21-22](level-21-22.md) |
| 22 → 23 |                                               | ✅ Done | [level-22-23](level-22-23.md) |
| 23 → 24 |                                               | ✅ Done | [level-23-24](level-23-24.md) |
| 24 → 25 |                                               | ✅ Done | [level-24-25](level-24-25.md) |
| 25 → 26 | Escaping a restricted shell via `more`/`vi`   | ✅ Done | [level-25-26](level-25-26.md) |
| 26 → 27 | Setuid helper after a shell escape            | ✅ Done | [level-26-27](level-26-27.md) |
| 27 → 28 | Cloning a Git repo over SSH                   | ✅ Done | [level-27-28](level-27-28.md) |
| 28 → 29 | Secrets in Git history                        | ✅ Done | [level-28-29](level-28-29.md) |
| 29 → 30 | Git branches                                  | ✅ Done | [level-29-30](level-29-30.md) |
| 30 → 31 | Git tags                                      | ✅ Done | [level-30-31](level-30-31.md) |
| 31 → 32 | Pushing to a remote, `.gitignore`             | ✅ Done | [level-31-32](level-31-32.md) |
| 32 → 33 | Escaping an uppercase shell                   | ✅ Done | [level-32-33](level-32-33.md) |

🏁 **Bandit complete:** level 33 is currently the last level of the game.

## Themes so far

- **Levels 0–6:** navigating the filesystem, and the tricky filenames that break naive commands.
- **Levels 7–11:** text processing: `grep`, `sort`, `uniq`, `strings`, `base64`, `tr`.
- **Level 12:** working out unknown file formats with `file`, one layer at a time.
- **Levels 13–21:** networking and authentication: SSH keys, ports, `nc`, TLS, setuid.
- **Levels 25–26, 32:** restricted shells, and the programs that let you out of them.
- **Levels 27–31:** Git: cloning over SSH, history, branches, tags, pushing.

See also the [cheatsheet](../resources/cheatsheet.md).

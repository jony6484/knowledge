1. change user and group
```bash
chmod 745 newfile.txt
```

| owner <br> | group | others |
| ---------- | ----- | ------ |
| rwx        | rwx   | rwx    |

| read | write | execute |
| ---- | ----- | ------- |
| 4    | 2     | 1       |
- **7** (4+2+1) = read, write, and execute
- **6** (4+2) = read and write
- **5** (4+1) = read and execute
- **4** = read only
- **3** (2+1) = write and execute
- **2** = write only
- **1** = execute only
- **0** = no permissions

| Mode | Owner | Group | Others | Typical use for scripts                                  |
| ---- | ----- | ----- | ------ | -------------------------------------------------------- |
| 700  | rwx   | ---   | ---    | Private script (only you can run/edit).                  |
| 711  | rwx   | --x   | --x    | Executable/traverse only; contents not readable.         |
| 744  | rwx   | r--   | r--    | You edit & run; others can read (not execute).           |
| 750  | rwx   | r-x   | ---    | Team-only executable; hidden from others.                |
| 754  | rwx   | r-x   | r--    | Exec for group, read-only for others.                    |
| 755  | rwx   | r-x   | r-x    | Common: everyone can run, only you edit.                 |
| 775  | rwx   | rwx   | r-x    | Shared within a group (both owner & group can edit/run). |

---
# Change owner

```bash
chown vboxuser sample.txt
```

```bash
chown [OPTIONS] new_owner[:new_group] folder_name
```

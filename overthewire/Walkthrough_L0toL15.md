# OverTheWire: Bandit Notes (L0–L15)

A compilation of my walkthrough notes for the Bandit wargame from OverTheWire. Good for CTF prep and showing off your terminal chops.

---

**L2 → L3**

```
Password: MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
What I learned: How to read hidden files and navigate directories.
```

**L3 → L4**

```
Password: 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
What I learned: Use of hidden file names with spaces and special characters.
```

**L4 → L5**

```
Password: 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
What I learned: How to use `find` with specific parameters like size and permissions to locate files.
Note: Used `find inhere/ -type f -size 1033c ! -executable` to locate the file.
```

**L5 → L6**

```
Password: HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
What I learned: Finding files by user, group, and size, plus using stderr redirection.
Command: find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
```

**L6 → L7**

```
Password: morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
What I learned: Suppressing permission denied messages with `2>/dev/null` and deep file search with `find`.
Note: Used stderr redirection `2>/dev/null` to hide permission errors.
```

**L7 → L8**

```
Password: dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
What I learned: Searching through files for known strings using `grep`.
```

**L8 → L9**

```
Password: 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
What I learned: Sorting and identifying unique entries with `sort` and `uniq -u`. Also learned how to pipe commands.
Command: `cat data.txt | sort | uniq -u`
```

**L9 → L10**

```
Password: FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
What I learned: Extracting readable strings from binary files using `strings`, and filtering with `grep`.
Command: `strings data.txt | grep =`
```

**L10 → L11**

```
Password: dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
What I learned: How to decode Base64 encoded content using `base64 -d`.
Command: `cat data.txt | base64 -d`
```

**L11 → L12**

```
Password: 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
What I learned: How to use the `tr` command for letter rotation (ROT13 cipher).
Command: `cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'`
```

**L12 → L13**

```
Password: FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn
What I learned: Creating temp dirs, reversing hexdumps, and identifying file formats before extracting them.
Commands:
- `mktemp -d` to make temp dir
- `xxd -r data.txt decodedfile`
- Use `file` to ID format, then unzip accordingly
```

**L13 → L14**

```
No direct password — SSH private key found.
What I learned: Managing SSH keys, setting file permissions, and logging in via SSH.
Commands:
- `chmod 600 sshkey.private`
- `ssh -i sshkey.private bandit14@localhost`
```

**L14 → L15**

```
Password: 8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo
What I learned: Using `nmap` to discover open ports and `nc` (netcat) to interact with services.
Commands:
- `cat /etc/bandit_pass/bandit14`
- `nmap -p 30000 localhost`
- `nc localhost 30000`
```

**L15 → L16**

```
Password: (not yet documented)
What I learned: How to initiate a secure TLS connection using `openssl s_client`. I ran `nmap -p 30001 localhost` to verify the port was open. Although not strictly necessary, it helped confirm the target. I realized `nc` and `telnet` wouldn’t work due to SSL/TLS encryption.

I used:
```bash
openssl s_client -connect localhost:30001

Notes//
This command started a TLS connection. Once connected, I had to manually paste the Level 15 password (the one I used to SSH into the box). This is because the server running on port 30001 is programmed to accept a password over an encrypted channel and return the Level 16 password if the input is correct.

```

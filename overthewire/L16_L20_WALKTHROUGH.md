# 🔐 Bandit Walkthrough: Levels 15 → 20

## ✅ L15 → L16  
**Password:** `kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx`  
**Commands Used:**
```bash
nmap -p 30001 --script ssl-enum-ciphers localhost
openssl s_client -connect localhost:30001
```
**What I Learned:**
- Used `nmap` to confirm the service on port 30001 is using SSL/TLS.
- `nc` (netcat) doesn't work with encrypted communication, so I used `openssl s_client` instead.
- The password prompt after connecting is for Bandit16, so I entered the password from L15 to access it.

---

## ✅ L16 → L17  
**Password:** *Found via RSA key extraction*  
**Commands Used:**
```bash
nmap -sV -p 31000-32000 localhost
echo "kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx" | openssl s_client -quiet -connect localhost:31790
vi /tmp/privatekey
chmod 400 /tmp/privatekey
ssh -i /tmp/privatekey bandit17@localhost -p 2220
```
**What I Learned:**
- `nmap -sV` detects service versions on a port range.
- The private RSA key was revealed through an SSL connection, then saved to a secure file.
- Used `chmod 400` to ensure only I can read the private key before using it with `ssh -i`.

---

## ✅ L17 → L18  
**Password:** `x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO`  
**Command Used:**
```bash
diff passwords.old passwords.new
```
**What I Learned:**
- `diff` quickly shows differences between two files — useful for config changes, secrets, logs, etc.
- Order doesn’t matter with `diff file1 file2` — it’ll show differences either way.

---

## ✅ L18 → L19  
**Password:** `cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8`  
**Command Used:**
```bash
ssh bandit18@bandit.labs.overthewire.org -p 2220 -t cat readme
```
**What I Learned:**
- The `.bashrc` auto-kicks you out, so the trick is to run a single command (`cat readme`) using `ssh -t`.
- You don’t *need* `-t` technically, but it ensures the command gets a pseudo-terminal, which helps in some edge cases.

🧠 **When to Apply:**  
Use this one-liner SSH trick when the remote shell auto-closes or gets hijacked (e.g., during CTFs or unstable environments).

---

## ✅ L19 → L20  
**Password:** `0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO`  
**Command Used:**
```bash
./bandit20-do cat /etc/bandit_pass/bandit20
```
**What I Learned:**
- The binary `bandit20-do` has the **setuid** bit set, meaning it runs as **bandit20**, even though you're logged in as bandit19.
- Passing a command like `cat` with the target file lets you read it with elevated privileges.

🧠 **When to Apply:**  
Setuid binaries are common privilege escalation vectors. If a binary is owned by a higher-privileged user and setuid is on, try feeding it benign commands (like `cat`, `ls`, etc.) to extract info.

Bandit Level 16 -> 17

Objective: Connect to a service running on port 31790 via SSL and provide the Level 16 password.

Key tools: nmap, openssl s_client

What worked:

openssl s_client -connect localhost:31790

On connection, input the Level 16 password when prompted.

The server responds with the password for Level 17.

Key gotcha: Non-SSL ports just returned the same message or closed the connection.

Tip: Use -quiet to simplify openssl output, but it’s not mandatory.

Bandit Level 17 -> 18

Objective: Figure out what’s changed between two password files.

Key tools: diff passwords.old passwords.new

Output: Only one line was different.

Solution: The new password is the one on the changed line in passwords.new.

Bandit Level 18 -> 19

Objective: The shell immediately logs you out.

Solution: SSH with a command:

ssh bandit18@bandit.labs.overthewire.org -p 2220 cat readme

This reads the password file without opening a full interactive shell.

Tip: -t flag for forcing pseudo-terminal isn’t necessary but sometimes helps for commands that require a terminal.

Bandit Level 19 -> 20

Objective: Use the bandit20-do binary with setuid permissions.

What you see:

The binary is owned by bandit20 but executable by bandit19.

Running it with a command spawns a process as bandit20.

Command used:

./bandit20-do cat /etc/bandit_pass/bandit20

This prints the password for Level 20.

Real-world parallel: Simulates privilege escalation by executing a program as another user (like sudo or SUID binaries).

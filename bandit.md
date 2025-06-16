# 🐧 Bandit Wargame Walkthrough – My Linux Journey (Level 0 → Level 20)

This is a record of my progress through the **Bandit Wargame** by OverTheWire. I learned essential commands and problem-solving techniques from Level 0 to Level 20.

---

## 🔰 Level 1 - level 20

### 🎯 Goal
Learn how to connect to a remote server via SSH.

### 💻 Command Used

```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220

🧠 Learned
How to use the ssh command to connect to a remote machine.

That -p specifies the port (2220 for Bandit). 



## 🔐 Level 1 → Level 2

 🎯 Goal: Read a file named -.

💻 Command Used:

cat ./-

🧠 Learned:
How to handle filenames that could be interpreted as options by prefixing them with ./.





## 🔓 Level 2 → Level 3

🎯 Goal: Read a file with spaces in its name.

💻 Command Used:

cat "spaces in this filename"

🧠 Learned:
How to use quotes to handle filenames with spaces.





## 🔒 Level 3 → Level 4

🎯 Goal: Find a hidden file called .hidden inside the inhere directory.

💻 Command Used:

ls -a inhere
cat inhere/.hidden

🧠 Learned:
How to use ls -a to reveal hidden files and read them.





## 🗝️ Level 4 → Level 5

🎯 Goal: Find a readable file in the inhere directory.

💻 Command Used:

file inhere/*
cat inhere/-file0X  # replace with the actual human-readable file

🧠 Learned:
How to identify readable files using file and open them.





## 🔑 Level 5 → Level 6

🎯 Goal: Find a 1033-byte file that is human-readable and not executable.

💻 Command Used:

find inhere/ -type f -size 1033c ! -executable -exec cat {} \;

🧠 Learned:
Advanced usage of find to filter files by size and permissions.





## 🛠️ Level 6 → Level 7

🎯 Goal: Find a 33-byte file owned by bandit7 and group bandit6.

💻 Command Used:

find / -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null
cat /path/to/file

🧠 Learned:
Using find with ownership and size conditions; suppressing errors.





## 🧩 Level 7 → Level 8

🎯 Goal: Find a line containing the word millionth in data.txt.

💻 Command Used:

grep millionth data.txt

🧠 Learned:
Basic text search using grep.





## 📂 Level 8 → Level 9

🎯 Goal: Find the only line that appears once in data.txt.

💻 Command Used:

sort data.txt | uniq -u

🧠 Learned:
Using sort and uniq to find unique entries.





## 🔎 Level 9 → Level 10

🎯 Goal: Extract a human-readable string from a binary file.

💻 Command Used:

strings data.txt | grep ==

🧠 Learned:
Using strings to extract readable content from a binary.






## 🕵️ Level 10 → Level 11

🎯 Goal: Decode a Base64 encoded password.

💻 Command Used:

base64 -d data.txt

🧠 Learned:
How to decode Base64 text using base64 -d.







## 🔍 Level 11 → Level 12

🎯 Goal: Decode a ROT13 encoded file.

💻 Command Used:

cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'

🧠 Learned:
Decoding ROT13 with tr.







## 📜 Level 12 → Level 13

🎯 Goal: Decompress and decode multiple layers of a hidden file.

💻 Command Used:

xxd -r data.txt > data
# then use file + correct decompression (gzip, bzip2, tar etc.) step by step

🧠 Learned:
Multi-step file recovery using hex reverse and compression tools.








## 🛡️ Level 13 → Level 14

🎯 Goal: Use SSH key to login as bandit14.

💻 Command Used:

ssh -i sshkey.private bandit14@localhost -p 2220

🧠 Learned:
Logging in with private SSH keys using ssh -i.






## 🔒 Level 14 → Level 15

🎯 Goal: Use Netcat to connect to a port and retrieve a password.

💻 Command Used:

echo <password> | nc localhost 30000

🧠 Learned:
Basic interaction with a TCP service using nc (Netcat).







## 🔑 Level 15 → Level 16

🎯 Goal: Connect to a secure SSL socket.

💻 Command Used:

echo <password> | openssl s_client -connect localhost:30001

🧠 Learned:
How to use OpenSSL to interact with secure services.







## 🛠️ Level 16 → Level 17

🎯 Goal: Scan multiple ports and find one returning the next password.

💻 Command Used:

for p in {31000..32000}; do echo <password> | nc localhost $p; done

🧠 Learned:
Using Bash loops and Netcat to scan ports.







## 🔐 Level 17 → Level 18

🎯 Goal: Find the difference between two files.

💻 Command Used:

diff passwords.new passwords.old

🧠 Learned:
How to use diff to compare files line-by-line.







## 🧩 Level 18 → Level 19

🎯 Goal: SSH auto-logout workaround to read a file.

💻 Command Used:

ssh bandit18@localhost -p 2220 cat readme

🧠 Learned:
Running remote commands directly over SSH.








## 🕵️ Level 19 → Level 20

🎯 Goal: Run a setuid binary with arguments.

💻 Command Used:

./bandit20-do cat /etc/bandit_pass/bandit20

🧠 Learned:
How to use setuid programs to run commands as another user.

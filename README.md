# Lab 1: Cryptographic Attacks: Brute Force and Traffic Analysis on Network Protocols


## Step 1: Enumerate the Vulnerable VM to Discover Usernames
Requirements

| Tool               | Purpose                        |
|--------------------|--------------------------------|
| Kali Linux         | Attacker machine               |
| Metasploitable 2   | Target/vulnerable machine      |
| Wordlist           | Password brute-forcing         |
| Nmap               | Port scanning                  |
| Hydra              | Brute force tool               |
| Burp Suite         | HTTP interception & testing    |
| enum4linux-ng      |                                |
---
## How to start

Got my metasploitable's IP address beforehand:
-in this case my metasploitables ip address is 192.168.18.132

![Screenshot 2025-04-11 114148](https://github.com/user-attachments/assets/e46ca9d7-de06-4805-9959-0d575431749d)

Performed a port scan using Nmap:

nmap -sV -A 192.168.18.132

![Screenshot 2025-04-11 113514](https://github.com/user-attachments/assets/f12b45e0-630f-43d6-b422-cbdfd93f749f)

enum4linux 192.168.10.132

![Screenshot 2025-04-15 132309](https://github.com/user-attachments/assets/f4b7dc2a-b9f6-44c3-9aab-3c6ae396ee77)

## Step 2: Perform Brute Force Attacks

switched on hydra which was pre installed in kali linux

![Screenshot 2025-04-15 132850](https://github.com/user-attachments/assets/4e05fd81-6395-406d-8d5f-858e368a825f)

#for the ftp attack
i then inserted the info required for the attack such as
- metasploits ip address: 192.168.10.132
- username to attack: msfadmin
- password : msfadmin

then i proceeded by pressing Y

![Screenshot 2025-04-15 133606](https://github.com/user-attachments/assets/3d83ec6d-a9fb-4a4c-a7b8-726568835445)


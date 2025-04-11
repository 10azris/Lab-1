# Lab 1: Cryptographic Attacks: Brute Force and Traffic Analysis on Network Protocols

## 🛠️ Requirements

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

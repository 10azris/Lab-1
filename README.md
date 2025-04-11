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
Performed a port scan using Nmap:

nmap -sV -A 192.168.18.132

   | Option              | Meaning                                                                                                                                       |
   |---------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
   | `nmap`              | Runs the Nmap network scanner tool.                                                                                                           |
   | `-sV`               | **Service/version detection** — Nmap will try to determine what software and version is running on each open port.                          |
   | `-p 21,23,22,80`    | Tells Nmap to scan **only** these specific ports: <br>• `21` = FTP <br>• `23` = Telnet <br>• `22` = SSH <br>• `80` = HTTP                    |
   | `[target-ip]`       | Replace with the IP address of the target/vulnerable machine you are scanning.

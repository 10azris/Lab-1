# Lab 1: Cryptographic Attacks: Brute Force and Traffic Analysis on Network Protocols


## Step 1: Enumerate the Vulnerable VM to Discover Usernames
Requirements

| Tool               | Purpose                        |
|--------------------|--------------------------------|
| Kali Linux         | Attacker machine               |
| Metasploitable 2   | Target/vulnerable machine      |
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

![Screenshot 2025-04-15 144526](https://github.com/user-attachments/assets/a3c0a099-70db-44e0-a7b3-92465dde276d)

![Screenshot 2025-04-11 113514](https://github.com/user-attachments/assets/f12b45e0-630f-43d6-b422-cbdfd93f749f)

enum4linux 192.168.10.132

![Screenshot 2025-04-15 144742](https://github.com/user-attachments/assets/930f1dc0-134b-4cbf-8618-34a59fd7da3a)

![Screenshot 2025-04-15 144830](https://github.com/user-attachments/assets/a6358b30-cc20-46aa-b4e4-ed8f89027b8a)

![Screenshot 2025-04-15 144906](https://github.com/user-attachments/assets/c667e651-cae5-46a3-9ed7-d8550dd1d860)

![Screenshot 2025-04-15 144943](https://github.com/user-attachments/assets/ab878b6b-f259-4de9-88a4-195d1bd796dd)

## Step 2: Perform Brute Force Attacks

created usernames before conducting the attack

![Screenshot 2025-04-15 143129](https://github.com/user-attachments/assets/6e34c307-b452-4443-ac33-579d66c40b5c)

switched on hydra which was pre installed in kali linux

![Screenshot 2025-04-15 132850](https://github.com/user-attachments/assets/4e05fd81-6395-406d-8d5f-858e368a825f)

#for the ftp attack
i then inserted the info required for the attack such as
- metasploits ip address: 192.168.18.132
- username to attack: msfadmin
- password : msfadmin

then i proceeded by pressing Y

![Screenshot 2025-04-15 133606](https://github.com/user-attachments/assets/3d83ec6d-a9fb-4a4c-a7b8-726568835445)

## FTP Brute Force using kali

![Screenshot 2025-04-15 143702](https://github.com/user-attachments/assets/a16f39b6-f19c-4d23-b80e-af7e89c4ce94)

## Telnet Brute Force using kali

![Screenshot 2025-04-15 144104](https://github.com/user-attachments/assets/38b2f84f-93da-488a-876b-ffc2671c3b64)

![Screenshot 2025-04-15 144210](https://github.com/user-attachments/assets/e2b8fc13-1576-4480-9b72-c4a1ec792b58)

## SSH Brute Force using NetExec

![Screenshot 2025-04-15 145308](https://github.com/user-attachments/assets/fbce218b-c0e1-457f-8686-215a7f9c848d)

## HTTP Login Brute Force Using Burp Suite



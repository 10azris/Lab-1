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

## HTTP Login Brute Force

Browse to http://192.168.18.132/

![Screenshot 2025-04-15 151147](https://github.com/user-attachments/assets/aef3e974-bc27-4d4d-8cd3-1279aba380dc)

i entered DVWA login page

![Screenshot 2025-04-15 151331](https://github.com/user-attachments/assets/f25d603e-a9f8-4e15-9df7-fc796d25f883)

![Screenshot 2025-04-15 151935](https://github.com/user-attachments/assets/1561347d-d7cd-45f6-a887-2ea14d445ecd)

## then login using the info
Username: admin
Password: password

![Screenshot 2025-04-15 152253](https://github.com/user-attachments/assets/3d7b45a9-cb46-40b3-a6a0-44c29fa8eddf)

go to DVWA security and choose low

![Screenshot 2025-04-15 152414](https://github.com/user-attachments/assets/6810567f-9931-4e7f-a36c-1dd79f83b567)

go into burp suite to find the proxy

![Screenshot 2025-04-15 161517](https://github.com/user-attachments/assets/4e395211-e6d5-426e-85b7-ac59c6a3193c)

i entered the proxy
127.0.0.1 and port 8080 from burp suite

![Screenshot 2025-04-15 161738](https://github.com/user-attachments/assets/60e021da-3303-4b0a-abae-abc42fc29feb)

## Problems Encountered
---
| Problem                                        | Solution               |
|------------------------------------------------|------------------------|
| wrongly wrote metasploitable ip                | found the right one    |
| changed proxy but burt suite didnt switch on   | changed the proxy      |
| enulinux had an error                          | used a different IP    |
---

## Mitigation Strategies
---
| Protocol   | Issue                     | Fix It With                             |
|------------|---------------------------|------------------------------------------
| FTP        | Data sent in plain text   | Use FTPS/SFTP                           |
| TELNET     | No encryption at all      | Disable it completely                   |
| HTTP       | Login info exposed        | Force HTTPS with valid certificate      |
| Passwords  | Too easy to guess         | Strong passwords + MFA + lockout policy |
---

## Conclusion
This lab helped me understand how common network protocols like FTP, TELNET, HTTP, and even SSH can be vulnerable if not configured properly. By using tools like Hydra, Burp Suite, and Wireshark, I was able to simulate real-world brute-force attacks, capture credentials, and analyze how data flows across a network.
The biggest takeaway is that protocols like FTP and TELNET are highly insecure because they transmit information in plain text. On the other hand, SSH provides strong encryption, which shows why it’s the preferred alternative.this lab taught me not just how to exploit weaknesses, but more importantly, how to defend against them using proper security practices like using encryption, enforcing strong passwords, and limiting access. These lessons are essential in real-world network security.

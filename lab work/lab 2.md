# Lab 2: Cryptographic Attacks, Cracking Weak Password Hashes and Exploiting Poor Authentication in Databases
---
# ✍️ Lab Tasks:

# 1. Service Enumeration and Initial Access ⚠️
- Identify the database service running on the target.
- Attempt to connect to the database service from Kali.
- Observe any errors during the connection attempt and investigate.

# 2. Enumeration of Users and Authentication Weakness ⚠️
- After gaining access, enumerate the database users.
- Determine which users have cryptographic authentication flaws.

Task:

- Identify any users with no passwords or weak access control.
- Attempt to authenticate using these accounts from Kali.

# 3. Password Hash Discovery and Hash Identification ⚠️
- Investigate available databases and identify any tables containing password hashes.
- Extract and list the hashes found.

# 4. Offline Hash Cracking ⚠️
- Attempt to crack the extracted hashes using tools of your choice (e.g., hashcat, john).
- Document the commands used, and which hashes were cracked.
- Analyze the entropy and strength of cracked passwords.

# 5. Cryptographic Analysis and Mitigation ⚠️
- Summarize the cryptographic issues identified:
- Authentication flaws
- Weak password hashing
- Transmission of data (if applicable)
- Propose secure alternatives, such as stronger hashing algorithms (e.g., bcrypt) and encrypted communication (SSL/TLS).
- Optional: Use Wireshark to check if any password/hash data is transmitted unencrypted.

---

# PART 1: Service Enumeration and Initial Access

- first i check for open ports
![Screenshot 2025-04-25 072516](https://github.com/user-attachments/assets/c9c43fb7-9353-4775-a8bd-b3c024b0a54a)

- next i tried connecting to the database
![Screenshot 2025-04-25 073307](https://github.com/user-attachments/assets/5cf1e0ae-cce1-4192-b361-289bfc16c9b0)

- i got an error as you can see
- Troubleshooted it by using this command

![Screenshot 2025-04-25 112151](https://github.com/user-attachments/assets/8d6ffa80-9f46-48f3-b462-c7139571a066)

Problem
- SSL error

the solution
- changed it to --skip-ssl

## Is accessing a database with no password a cryptographic failure? ❓ 
Yes.
Allowing access without a password bypasses authentication and violates cryptographic principles. It fails to enforce confidentiality, integrity, and secure access control.
# PART 2: User Enumeration & Authentication Flaws

- i connected the database to dvwa
![Screenshot 2025-04-25 114736](https://github.com/user-attachments/assets/65a241f9-7ef4-4db7-8ccb-f2d955273031)

---

![Screenshot 2025-04-25 114806](https://github.com/user-attachments/assets/e3c78f1a-540b-4ed3-bb46-5e825e056d3e)

# PART 3: Password Hash Discovery & Hash Type Identification

- i listed all the databases
![Screenshot 2025-04-25 115547](https://github.com/user-attachments/assets/64b51d7c-bd00-4d89-9ec9-949e71d12d5b)

- im using the dvwa database
![Screenshot 2025-04-25 120254](https://github.com/user-attachments/assets/9d4047fd-1f16-4123-8d8c-e9c9719dd4d0)

![Screenshot 2025-04-25 120358](https://github.com/user-attachments/assets/ea8831e5-d906-483f-b0db-4dc68e767eb3)

- i found tables with info
![Screenshot 2025-04-25 120459](https://github.com/user-attachments/assets/ab8f7442-df67-4fba-be06-c9b156697bf6)

- for the password i chose is Gordon's which is
e99a18c428cb38d5f260853678922e03

- then go to a directory, in this case i chose Pictures
![Screenshot 2025-04-25 120936](https://github.com/user-attachments/assets/820d8eef-75a2-4a52-94fd-d175940cb956)

- then i entered the vim for hashes.txt
---
![Screenshot 2025-04-25 121432](https://github.com/user-attachments/assets/1820bc53-60fe-45e6-9966-d55aa3dff694)

- pasted the hash password i took from Gordon
---
![Screenshot 2025-04-25 121918](https://github.com/user-attachments/assets/bbc67694-c48e-465c-a65b-b448c4773d34)

- Used hashid
![Screenshot 2025-04-25 122716](https://github.com/user-attachments/assets/669065cb-ed0c-48b9-89e6-7d2b864e5c93)

## What cryptographic weaknesses exist in this hashing method? ❓

1. Use of weak algorithms example MD5
2. vulnerable to rainbow table attacks
3. No key which makes it easy to brute force

# PART 4: Offline Hash Cracking

- crack it using john the ripper

![Screenshot 2025-04-25 125451](https://github.com/user-attachments/assets/c2fb032f-6afa-4220-88bc-29ac444ba3e5)
- I used the possible password lists

![Screenshot 2025-04-25 125813](https://github.com/user-attachments/assets/a842e111-0f84-49bd-97b6-3c3d3ff7c2d5)
- i added the format to the command because there previously was an error

- wasn't able to crack the hash so began to troubleshoot
![Screenshot 2025-04-25 131152](https://github.com/user-attachments/assets/a07de59b-6360-455c-a0eb-68c47531e5e0)

- at last i was able to crack the hash
![Screenshot 2025-04-25 131329](https://github.com/user-attachments/assets/6769fe59-91fd-4ddd-8420-afb8ddcd82c1)

- which was abc123.

# PART 5: Cryptographic Analysis and Mitigation

## Cryptographic Vulnerabilities & Fixes

here are the issues i encountered and how to mitigate them.

| Issue          | Risk                          | Solution                  |
|----------------|-------------------------------|---------------------------|
| MD5 Hashing    | Easily cracked                | Use bcrypt/Argon2         |
| No Salting     | Rainbow table attacks         | Add unique salts          |
| Weak Passwords | Quick brute-force compromise  | Enforce 12+ char passwords|
| No Encryption  | MITM attacks                  | Enforce HTTPS/TLS 1.2+    |

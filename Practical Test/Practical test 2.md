# Practical Test 2

## 📌 Scenario

🔐 Ransomware is a malicious real-world application of cryptography. In this exercise, you will act as a cryptography and malware reverse engineer, tasked with analyzing a suspicious binary that simulates ransomware behavior. Your job is to analyze, extract, and break the cryptography used in this malware, and then write a decryption script to recover the victim's files, and save the world.

---

## 🎯 Your Tasks

1. Static Analysis and Reverse Engineering
1. Identify the programming language or packaging tool used.
2. Reverse engineer the binary to recover the source
3. Identify the encryption algorithm and mode used.
4. Recover the encryption key.
5. Analyze cryptographic implementation
6. Describe any flaws, and misuse of cryptography in the binary.

2. Decryption Tool Development (Recover the Victim Files)

Use your understanding to write a working Python script (decrypt.py):

1. Uses the extracted key, algorithm, and mode.
2. Correct key, padding, IV, etc.
3. Correctly decrypts the .enc files
4. and recover the original plaintext

---

3. Flaw Analysis

1. Explain how and why the cryptography used in the ransomware is flawed.
2. Suggest what a more secure version of encryption could look like.

---

first

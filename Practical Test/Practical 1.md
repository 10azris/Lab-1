# Practical Test 1


first, i enabled ssh and finished prepping

![Screenshot 2025-05-16 195239](https://github.com/user-attachments/assets/7cca7a70-6693-4d84-a3e6-d43afae5f3f4)


---

## 🛠️ Task 1: Generate Your GPG Key Pair

next i opened kali and generated the key

``gpg --full-generate-key``

![Screenshot 2025-05-16 195512](https://github.com/user-attachments/assets/868b8d84-2923-47f4-a52b-14d1f3f529db)

choices of keys popped up and i chose number 1

``Please select what kind of key you want:
1 = RSA and RSA (default)``

![Screenshot 2025-05-16 195659](https://github.com/user-attachments/assets/dceb3b22-4bf3-4b6a-94c5-d80f316b3f3d)

then i chose my keysize which is 3073 long

``3073``

![Screenshot 2025-05-16 200042](https://github.com/user-attachments/assets/73cdae2a-9607-4e68-8788-8f0717a78422)

next i chose the expiry date

``Key is valid for? (0) 1y``

![Screenshot 2025-05-16 200310](https://github.com/user-attachments/assets/9110e32a-5bde-4475-b4e0-408daaefa963)

i entered my credentials such as,
1. name
2. email
3. comment

![Screenshot 2025-05-16 200702](https://github.com/user-attachments/assets/f3fee914-84ce-4971-a54f-5258b202693a)

then i was told to insert a paraphrase

``azris`` was my paraphrase

![Screenshot 2025-05-16 200810](https://github.com/user-attachments/assets/4a0fb9c7-5870-4786-99c5-fd00e668c7ca)

![Screenshot 2025-05-16 200931](https://github.com/user-attachments/assets/b49d2386-51b4-4511-880a-ed9358e3cb56)

then i tested it out using

``gpg --list-keys``

and this is the output i got

![Screenshot 2025-05-16 201048](https://github.com/user-attachments/assets/c19dde3a-9425-447b-9290-4095edf9559d)


---


## 🔓 Task 2: Encrypt and Decrypt a File

im gonna create a file using this command

``echo "This file was encrypted by Your Name (Your Student ID)" > message.txt``

![Screenshot 2025-05-16 201337](https://github.com/user-attachments/assets/6be1756a-3356-4fd2-b100-9cd2c7e66bd0)

next im gonna encrypt the file using my public key

``gpg --encrypt --recipient "Your Name" message.txt``

![Screenshot 2025-05-16 201629](https://github.com/user-attachments/assets/13709791-67dd-460c-80a3-85909371e30b)

then im gonna decrypt the file using

``gpg --output decrypted.txt --decrypt message.txt.gpg``

as i try to decrypt it im asked for my paraphrase i previously inserted

![Screenshot 2025-05-16 201819](https://github.com/user-attachments/assets/6aa051b7-f723-49fd-b3cc-4482a34fe812)

after i put in my paraphrase which was 

``azris``

![Screenshot 2025-05-16 201919](https://github.com/user-attachments/assets/5cfd4dfd-8ed5-4002-bbfc-ce0db97cf431)

my message got encrypted

then i verified the message

``cat decrypted.txt``

![Screenshot 2025-05-16 202132](https://github.com/user-attachments/assets/3ff1c21a-1c60-4d67-bebf-e5a8a1df5664)


---
## ✍️ Task 3: Sign and Verify a Message

first i created a sign message

``echo "I, Your Name, declare this is my work." > signed_message.txt``

![Screenshot 2025-05-16 202558](https://github.com/user-attachments/assets/8c5cb3f3-769a-4c44-8e33-036bcf2daf67)

next i'll sign the file

``gpg --clearsign signed_message.txt``

![Screenshot 2025-05-16 202800](https://github.com/user-attachments/assets/bf3f3e99-c4b0-4bd2-bff5-12381574a2a3)

after that i'll verify the signature

``gpg --verify signed_message.txt.asc``

![Screenshot 2025-05-16 202927](https://github.com/user-attachments/assets/dd9cc37e-c25a-4071-8c7f-447ce3ba0d5e)


---
## 🔑 Task 4: Configure Passwordless SSH Authentication

i'll generate the SSH key

``ssh-keygen -t rsa -b 4096 -C "Your Name-YourID"``

![Screenshot 2025-05-16 203359](https://github.com/user-attachments/assets/07cb936f-a6be-4c37-a219-7041f729cf98)

i chose the default location with no paraphrase

![Screenshot 2025-05-16 203442](https://github.com/user-attachments/assets/5039f25c-ba61-4c53-b3f2-5a7cb8197400)

then i viewed my public key using

``cat ~/.ssh/id_rsa.pub``

![Screenshot 2025-05-16 203537](https://github.com/user-attachments/assets/4b8b57b3-0c80-443c-a08c-301073cefe4d)

I added public key to authorized keys

``cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys
chmod 600 ~/.ssh/authorized_keys
chmod 700 ~/.ssh``

![Screenshot 2025-05-16 203820](https://github.com/user-attachments/assets/438acfb1-50f6-40d3-9211-5930c344895f)

Then i Tested passwordless login

![Screenshot 2025-05-16 204005](https://github.com/user-attachments/assets/644dfca0-ba07-48e2-84b8-e6857a9dd54a)

![Screenshot 2025-05-16 204043](https://github.com/user-attachments/assets/d78752b7-7f1c-45e4-bc54-28c64d4e7e36)

Then i created a file via SSH

``ssh localhost "echo Your_Student_ID > Your_Name.txt"``

![Screenshot 2025-05-16 204208](https://github.com/user-attachments/assets/336ba1a0-257f-4d30-a3a3-7b188f1e6a55)

next im gonna check the file

``ls
cat Your_Name.txt``

![Screenshot 2025-05-16 204349](https://github.com/user-attachments/assets/7781fe06-14ff-4c02-91ec-cf20e1ad67bd)


---


## 🕵️ Task 5: Hash Cracking Challenge
Objective: Crack provided hashes.

- Hashes Provided (Variety of types):

- SnZlcmV4IEF2IEpmcmNyZSBFeiBCcnJl
- 6283293831c84671546324c9373704ca
- 2bc92f33a2ede5ada3d65b468a81f617d0229d843d87c63313833e509e5a6782

first Using Kali Linux's built in base64 decoding i got

``Jverex Av Jfrcrre Ez Brre``

![Screenshot 2025-05-16 205830](https://github.com/user-attachments/assets/70a465ad-d33a-480c-a896-5b1bd4352e15)

it is ROT13 encoded text

``wireless network security``




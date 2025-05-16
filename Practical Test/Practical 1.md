# Practical Test 1
first, i enabled ssh and finished prepping

![Screenshot 2025-05-16 195239](https://github.com/user-attachments/assets/7cca7a70-6693-4d84-a3e6-d43afae5f3f4)

## Task 1: Generate Your GPG Key Pair

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

## Task 2: Encrypt and Decrypt a File
## Task 3: Sign and Verify a Message
## Task 4: Configure Passwordless SSH Authentication
## Task 5: Hash Cracking Challenge
Objective: Crack provided hashes.

- Hashes Provided (Variety of types):

- SnZlcmV4IEF2IEpmcmNyZSBFeiBCcnJl
- 6283293831c84671546324c9373704ca
- 2bc92f33a2ede5ada3d65b468a81f617d0229d843d87c63313833e509e5a6782

# Lab 3: Hands-on Exploration of Cryptographic Tools: Hashing, Encryption, and Digital Signatures

# Part 1: Encrypt and Decrypt a File Symmetric Encryption with AES ✍️
---

1. first i made a strong key

openssl rand -hex 32 > key.txt

![Screenshot 2025-05-01 171542](https://github.com/user-attachments/assets/51f16934-5df4-4544-93f9-705fbc55d36a)

2. then i made a message file

echo "ola amigo" amigo.txt

![Screenshot 2025-05-01 172042](https://github.com/user-attachments/assets/c9241de0-5170-4ad1-b14f-8007a1c70349)

3. then i locked the message using my secret key

openssl enc -aes-256-cbc -salt -in amigo.txt -out amigo.txt.enc -pass file:./key.txt

![Screenshot 2025-05-01 172444](https://github.com/user-attachments/assets/2eccbdfe-5b60-400c-bbcb-9037da2bf334)

4. i unlocked the message

openssl enc -d -aes-256-cbc -in amigo.txt.enc -out amigo_decrypted.txt -pass file:./key.txt

![Screenshot 2025-05-01 172542](https://github.com/user-attachments/assets/324dff10-a889-4f41-86f3-b046218a7e5d)

5. i checked the files

cat amigo.txt
cat amigo_decrypted.txt

![Screenshot 2025-05-01 172644](https://github.com/user-attachments/assets/23ec88ad-144b-4c00-9c97-4ece5211c5d1)
---
![Screenshot 2025-05-01 172656](https://github.com/user-attachments/assets/71133760-9af0-40ae-8f1e-c541528bdb4d)

6. the message encrypted

![Screenshot 2025-05-02 071328](https://github.com/user-attachments/assets/6776bc5a-475c-4a97-b7d7-18c122bafd49)

---

# Part 2: Asymmetric Encryption and Decryption using RSA 👻
---

1. I made a private key

openssl genpkey -algorithm RSA -out private.pem -pkeyopt rsa_keygen_bits:2048

![Screenshot 2025-05-02 073057](https://github.com/user-attachments/assets/04942644-46bc-46c8-b6cc-655a0ae8eedf)

2. then a public key

openssl rsa -pubout -in private.pem -out public.pem

![Screenshot 2025-05-02 073112](https://github.com/user-attachments/assets/65d25c39-0b99-4ca0-9659-a55d92009af3)

3. i then wrote a message

echo "naruto run to area 51" > naruto.txt

![Screenshot 2025-05-02 073130](https://github.com/user-attachments/assets/67252da1-deb1-4152-99da-3e42004bcfef)

4. i encrypted the message using my public key

openssl pkeyutl -encrypt -pubin -inkey public.pem -in naruto.txt -out naruto.enc

![Screenshot 2025-05-02 073144](https://github.com/user-attachments/assets/ba9a8774-92cf-4657-9124-346738eeb7b8)

7. i decrypted the message using my private key

openssl pkeyutl -decrypt -inkey private.pem -in naruto.enc -out naruto_decrypted.txt

![Screenshot 2025-05-02 073158](https://github.com/user-attachments/assets/f1ed49de-38c6-42bc-9691-d0f0f2c88f89)

8. i checked the files

cat naruto.txt & cat naruto_decrypted.txt

![Screenshot 2025-05-02 073900](https://github.com/user-attachments/assets/a476bbf7-f916-4569-9a58-9dbf03699d87)

# Part 3: Hashing and Message Integrity using SHA-256 🍇
---

1. i made a file

echo "don't blink" > blink.txt 

![Screenshot 2025-05-02 075811](https://github.com/user-attachments/assets/9df4aaa8-02a6-479b-8fd1-f7c2934ac34a)

2. i made a SHA-256

openssl dgst -sha256 blink.txt  

![Screenshot 2025-05-02 075916](https://github.com/user-attachments/assets/436fdbd3-df72-47f7-bc1e-d582c49b04a3)

3. then i changed the file

echo "real zies." >> blink.txt

![Screenshot 2025-05-02 080137](https://github.com/user-attachments/assets/4ffe557a-4599-49df-8d16-763eace6e0f2)

4. after that i checked the SHA again

openssl dgst -sha256 blink.txt

![Screenshot 2025-05-02 080211](https://github.com/user-attachments/assets/048ef96c-f543-464c-91c4-4039559715e7)

# Part 4: Digital Signatures using RSA 🍔
---

1. i used my private key

echo "Fly to the moon." > moon.txt     

![Screenshot 2025-05-02 132940](https://github.com/user-attachments/assets/98c50754-524a-4399-880f-a6ec4ae56a35)

2. then Signed teh file

openssl dgst -sha256 -sign private.pem -out moon.sig moon.txt

![Screenshot 2025-05-02 133249](https://github.com/user-attachments/assets/ad85809f-543c-40a4-bb1f-082ccffae02e)

3. later i verified the signature

openssl dgst -sha256 -verify public.pem -signature moon.sig moon.txt 

![Screenshot 2025-05-02 133356](https://github.com/user-attachments/assets/60a238c2-7c93-43d6-b0e0-dfc7f0fa81d0)

4. then i tampered with the file

echo "bulan" >> moon.txt

![Screenshot 2025-05-02 133456](https://github.com/user-attachments/assets/0aee9acd-50a0-437f-bb4e-801c8f0be941)

5. and tried to verify it again

openssl dgst -sha256 -verify public.pem -signature moon.sig moon.txt

![Screenshot 2025-05-02 133542](https://github.com/user-attachments/assets/87b5dc13-567c-4bc1-90e1-2368517f5afe)

## Trubleshooting ☂️

here are the issues i encountered and how to solve them.

| Issue                  | Solution                                    |
|------------------------|---------------------------------------------|
| wrong file name        | make sure name is correct                   |
| verification error     | do not mess with file before verification   |
| wrong password         | check the key                               |


# 🧪 Lab 4: Implementing Cryptography with Python
---

## 📌 Objective
1. Learn core cryptographic operations using Python.
2. Practice symmetric (AES) and asymmetric (RSA) encryption.
3. Understand hashing and digital signatures.
4. Verify data integrity and authenticity through hands-on coding.

---

first i downloaded pycryptodome

![Screenshot 2025-05-08 093454](https://github.com/user-attachments/assets/c6fa1176-e2ec-46b8-abd5-d68b3f3c9d57)

## 🔐 Part 1: Symmetric Encryption using AES-256-CBC

first i inserted the code for AES encryption

![Screenshot 2025-05-08 110807](https://github.com/user-attachments/assets/7554307e-4eea-4522-bd11-2799f80f00a7)

then naim inserted the code for AES decryption

![Screenshot 2025-05-08 110907](https://github.com/user-attachments/assets/23dc642d-8778-4b94-b015-0ef87648599c)

later i added code to allow us to input a message

![Screenshot 2025-05-08 111151](https://github.com/user-attachments/assets/ce8ae855-fe67-47b4-a4fd-9c92fbb51ec9)

the full code looks like this

```
from Crypto.Cipher import AES
from Crypto.Random import get_random_bytes
import base64

key = get_random_bytes(32)
iv = get_random_bytes(16)

def pad(data):
    pad_len = 16 - len(data) % 16
    return data + bytes([pad_len]) * pad_len

def unpad(data):
    pad_len = data[-1]
    return data[:-pad_len]

def encrypt_aes(plaintext):
    cipher = AES.new(key, AES.MODE_CBC, iv)
    padded = pad(plaintext.encode())
    ciphertext = cipher.encrypt(padded)
    return base64.b64encode(ciphertext).decode()

def decrypt_aes(cipher_b64):
    cipher = AES.new(key, AES.MODE_CBC, iv)
    ciphertext = base64.b64decode(cipher_b64)
    padded_plaintext = cipher.decrypt(ciphertext)
    return unpad(padded_plaintext).decode()

user_msg = input("Enter a message to encrypt with AES: ")
cipher_text = encrypt_aes(user_msg)
print("Encrypted:", cipher_text)
print("Decrypted:", decrypt_aes(cipher_text))

```

![Screenshot 2025-05-08 103759](https://github.com/user-attachments/assets/fd37b3d7-6c5e-459e-a824-a6d4b788885e)

here is the output

![Screenshot 2025-05-08 112212](https://github.com/user-attachments/assets/6fc9cc6b-286d-4ee7-9182-924f0d56f106)

## 🔑 Part 2: Asymmetric Encryption using RSA

first i inserted the code for RSA encryption

![Screenshot 2025-05-08 113034](https://github.com/user-attachments/assets/e2d9cb4d-3d1a-4fad-af9f-693af0ff2847)

then naim inserted the code for AES decryption

![Screenshot 2025-05-08 113124](https://github.com/user-attachments/assets/20e4d3e4-763c-4263-be41-74ced2128400)

later i added code to allow us to input a message

![Screenshot 2025-05-08 113509](https://github.com/user-attachments/assets/5d77f043-ebe2-4b0c-89fe-169cea74fd96)

the full code looks like this

```
from Crypto.PublicKey import RSA
from Crypto.Cipher import PKCS1_OAEP

key = RSA.generate(2048)
public_key = key.publickey()
private_key = key

def encrypt_rsa(message):
    cipher = PKCS1_OAEP.new(public_key)
    return cipher.encrypt(message.encode())

def decrypt_rsa(ciphertext):
    cipher = PKCS1_OAEP.new(private_key)
    return cipher.decrypt(ciphertext).decode()

user_msg = input("Enter a message to encrypt with RSA: ")
rsa_encrypted = encrypt_rsa(user_msg)
print("Encrypted RSA:", rsa_encrypted)
print("Decrypted RSA:", decrypt_rsa(rsa_encrypted))

```

![Screenshot 2025-05-08 113551](https://github.com/user-attachments/assets/d5f907c7-21f5-4334-b3f5-2d16f204aa1f)

here is the output

![Screenshot 2025-05-08 113629](https://github.com/user-attachments/assets/e358988e-7cd9-4347-86ad-d4e03cc73691)

## 🔄 Part 3: Hashing and Message Integrity using SHA-256

i put in the code to encode the message in SHA

![Screenshot 2025-05-08 114535](https://github.com/user-attachments/assets/881a61d8-e0e5-4ff8-92c3-82be23b717e9)

the full code looks like this

```
from Crypto.Hash import SHA256

def hash_message(message):
    hash_obj = SHA256.new(message.encode())
    return hash_obj.hexdigest()

user_msg = input("Enter a message to hash using SHA-256: ")
hashed = hash_message(user_msg)
print("SHA-256 Hash:", hashed)

```

![Screenshot 2025-05-08 113953](https://github.com/user-attachments/assets/a53af610-1661-4b12-bcb1-9879ea44274b)

here is the output

![Screenshot 2025-05-08 114645](https://github.com/user-attachments/assets/f5fd91d9-afcd-44ef-a0b0-7e94f8c0d628)

## ✍️ Part 4: Digital Signatures using RSA & SHA-256

first i inserted the code for the private and public key

![Screenshot 2025-05-08 121601](https://github.com/user-attachments/assets/ade7bf3f-d25c-4e68-bf35-448c9b877bc4)

then i inserted the code to sign the message

![Screenshot 2025-05-08 121729](https://github.com/user-attachments/assets/146c6eb6-de44-467d-802f-ef110c053bc2)

after that i inserted the code to verify the signature

![Screenshot 2025-05-08 121849](https://github.com/user-attachments/assets/f7609d9e-fa62-481e-9562-4985b1ecbd00)

next i inserted the code to input the message and verify the validity of the sign

![Screenshot 2025-05-08 121929](https://github.com/user-attachments/assets/cac76f0c-2a76-4a30-b26a-0b0099da2e03)

the full code looks like this

```
from Crypto.PublicKey import RSA
from Crypto.Signature import pkcs1_15
from Crypto.Hash import SHA256


key = RSA.generate(2048)
private_key = key
public_key = key.publickey()


def sign_message(message):
    hash_obj = SHA256.new(message.encode())
    return pkcs1_15.new(private_key).sign(hash_obj)


def verify_signature(message, signature):
    hash_obj = SHA256.new(message.encode())
    try:
        pkcs1_15.new(public_key).verify(hash_obj, signature)
        return True
    except (ValueError, TypeError):
        return False


user_msg = input("Enter a message to digitally sign: ")
signature = sign_message(user_msg)
print("Signature (hex):", signature.hex())


is_valid = verify_signature(user_msg, signature)
print("Signature Verified:", is_valid)

```

![Screenshot 2025-05-08 120435](https://github.com/user-attachments/assets/c30582bd-c105-41ad-84c8-055203ecfacc)

here is the output

![Screenshot 2025-05-08 120454](https://github.com/user-attachments/assets/13d4fc9e-2757-45d3-bc0a-9849edc73fdd)


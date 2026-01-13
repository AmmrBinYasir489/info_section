# Information Security – Complete Final Exam Notes

---

## 1. Diffie–Hellman Key Exchange (DH)

### Definition

Diffie–Hellman is a **key exchange algorithm** used to securely generate a **shared secret key** over an insecure channel. It does **not encrypt messages**, it only helps both parties agree on the same secret key.

---

### Working (Your Given Example Explained)

**Step 1: Public Parameters**

* Prime number **P = 23**
* Generator **G = 9**

These values are public and known to everyone.

---

**Step 2: Private Keys**

* Alice chooses private key **a = 4**
* Bob chooses private key **b = 3**

Private keys are **never shared**.

---

**Step 3: Public Key Calculation**

* Alice computes:

  x = G^a mod P = 9^4 mod 23 = 6

* Bob computes:

  y = G^b mod P = 9^3 mod 23 = 16

These values are public.

---

**Step 4–5: Exchange Public Values**

* Alice sends **x = 6** to Bob
* Bob sends **y = 16** to Alice

---

**Step 6: Shared Secret Calculation**

* Alice computes:

  k = y^a mod P = 16^4 mod 23 = 9

* Bob computes:

  k = x^b mod P = 6^3 mod 23 = 9

---

### Final Result

Both Alice and Bob get the **same secret key = 9**

✔ Secure key exchange achieved

---

### Why DH is Secure?

* Private keys are never transmitted
* Discrete logarithm problem is computationally hard

---

## 2. RSA Algorithm

### Definition

RSA is an **asymmetric encryption algorithm** used for:

* Encryption / Decryption
* Digital Signatures
* Key Exchange

It uses **two keys**:

* Public Key (encryption)
* Private Key (decryption)

---

## RSA Key Generation Steps

### Step 1: Choose Two Prime Numbers

Let:

* p = 61
* q = 53

---

### Step 2: Compute n

n = p × q = 61 × 53 = 3233

---

### Step 3: Compute Totient (φ)

φ(n) = (p − 1)(q − 1)
φ(n) = 60 × 52 = 3120

---

### Step 4: Choose Public Key e

Conditions:

* 1 < e < 3120
* gcd(e, 3120) = 1

Choose:

* e = 17

---

### Step 5: Compute Private Key d

Find **d** such that:

d × e ≡ 1 (mod 3120)

Result:

* d = 2753

---

### RSA Keys

* **Public Key** = (e = 17, n = 3233)
* **Private Key** = (d = 2753, n = 3233)

---

## RSA Encryption & Decryption

### Encryption Formula

C = M^e mod n

### Decryption Formula

M = C^d mod n

---

### Example

Message:
M = 65

Encryption:
C = 65^17 mod 3233 = 2790

Decryption:
M = 2790^2753 mod 3233 = 65

✔ Original message recovered

---

## 3. Hash Functions

### Definition

A hash function converts **variable-length input** into a **fixed-length output**.

Example:

* Password → Hash value

---

### Properties

* Fixed output size
* Fast computation
* One-way function

---

### One-Way Hash Function

* Cannot be reversed
* Used in password storage

---

### Password Hashing Example

Password: apple
Hash: A7 6D 8B 99

Passwords are **never stored in plain text**.

---

## 4. Password Salting

### Problem Without Salt

Same passwords → same hash

### Solution: Salt

Random value added to password before hashing

Hash = H(Salt + Password)

---

### Example

H("9195 + apple") = 92 C6 13 C1

✔ Prevents rainbow table attacks

---

## 5. Digital Signatures

### Definition

A digital signature provides:

* Authentication
* Integrity
* Non-repudiation

---

### Working

1. Document is hashed
2. Hash is encrypted with sender’s private key
3. Receiver decrypts using public key
4. Hash values compared

---

## 6. Hash Collisions

### Definition

When two different inputs produce the **same hash output**.

---

### Collision Resistance

A good hash function makes collisions **computationally infeasible**.

---

## 7. Cryptographic Hash Functions

### Definition

A cryptographic hash function is:

* One-way
* Collision-resistant

---

### Examples

* MD5 (128-bit)
* SHA-1 (160-bit)
* SHA-256 (256-bit)

---

## 8. Authentication

### Definition

Authentication verifies:

* Identity of user
* Integrity of data

---

### Examples

* ATM PIN
* Login passwords
* Digital certificates

---

## 9. Kerberos (Overview)

### Definition

Kerberos is a **network authentication protocol** using **tickets** and **symmetric keys**.

---

### Main Components

* Client
* Authentication Server (AS)
* Ticket Granting Server (TGS)
* Service Server

---

### Advantages

* No password sent over network
* Mutual authentication

---

## 10. Stream Ciphers

### Definition

Stream ciphers encrypt data **bit-by-bit or byte-by-byte**.

---

### Examples

* RC4
* Salsa20

---

### Advantages

* Fast
* Low memory usage

---

## FINAL EXAM TIP

✔ Definitions yaad rakho
✔ Steps sequence mein likho
✔ Numerical examples zaroor show karo
✔ Formulas highlight karo

---

If you want:

* Short exam answers
* MCQs
* Numericals practice
* Slides-wise explanation

Just tell me 👍

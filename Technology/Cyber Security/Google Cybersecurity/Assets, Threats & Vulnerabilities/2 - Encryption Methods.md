
# Encryption Methods

## Contents :-

#### [2.01 - Cryptography Fundamentals](#201---cryptography-fundamentals)
#### [2.02 - Encryption Algorithms](#202---encryption-algorithms)
#### [2.03 - Hashing](#203---hashing)

---

## 2.01 - Cryptography Fundamentals <a name="201---cryptography-fundamentals"></a>

- **PII**(***Personally Identifiable Information***) - any information that can be used to infer an individual's identity
- **Cryptography** - process of transforming information into a form that unintended readers can't understand.
- **Algorithm** - a set of rules that can solve a problem
- **Cipher** - an algorithm that encrypts information
- **Cryptographic Key** - a mechanism that decrypts ciphertext

### 2.01.01 - PKI (Public Key Infrastructure)

**PKI**(***Public Key Infrastructure***) is an encryption framework that secures the exchange of information online.

- **Asymmetric Encryption** - uses public and private key pair for encryption and decryption of data. The public key is used to encrypt data, and the private key decrypts it.

- **Symmetric Encryption** - uses a single secret key for encryption and decryption of data. Because it uses one key for encryption and decryption, the sender and receiver must know the secret key to lock or unlock the cipher.

- **Digital Certificate** - a file that verifies the identity of a public key holder

#### PKI Process:

1. Exchange of encrypted information 
2. Establish trust using a system of digital certificates

#### Importance of key length

- Ciphers are vulnerable to brute force attacks, which use a trial and error process to discover private information. This tactic is the digital equivalent of trying every number in a combination lock trying to find the right one. 
- In modern encryption, longer key lengths are considered to be more secure as it leads to more possibilities that an attacker needs to try to unlock a cipher.
- One drawback to having long encryption keys is slower processing times.

---

## 2.02 - Encryption Algorithms <a name="#202---encryption-algorithms"></a>

### 2.02.01 - Symmetric algorithms

1. **3DES**
	- **3DES**(***Triple DES***) is known as a block cipher because of the way it converts plaintext into ciphertext in “blocks.” 
	- Its origins trace back to the **DES**(***Data Encryption Standard***), which was developed in the early 1970s. DES was one of the earliest symmetric encryption algorithms that generated 64-bit keys. 
	- A bit is the smallest unit of data measurement on a computer. Triple DES generates keys that are 192 bits, or three times as long. 
	- Despite the longer keys, many organizations are moving away from using Triple DES due to limitations on the amount of data that can be encrypted. However, Triple DES is likely to remain in use for backwards compatibility purposes.   

2. **AES**
	- **AES**(***Advanced Encryption Standard***) is one of the most secure symmetric algorithms today. 
	- AES generates keys that are 128, 192, or 256 bits. Cryptographic keys of this size are considered to be safe from brute force attacks. 
	- It’s estimated that brute forcing an AES 128-bit key could take a modern computer billions of years!

### 2.02.02 - Asymmetric algorithms

1. **RSA**
	- **RSA**(***Rivest Shamir Adleman***) is named after its three creators who developed it while at the MIT(Massachusetts Institute of Technology). 
	- RSA is one of the first asymmetric encryption algorithms that produces a public and private key pair. 
	- Asymmetric algorithms produce even longer key lengths due to the fact that these functions are creating two keys. RSA key sizes are 1,024, 2,048, or 4,096 bits. 

2. **DSA**
	- **DSA**(***Digital Signature Algorithm***) is a standard asymmetric algorithm that was introduced by NIST in the early 1990s. 
	- DSA also generates key lengths of 2,048 bits. 
	- This algorithm is widely used today as a complement to RSA in public key infrastructure.

### 2.02.03 - Generating keys

- These algorithms must be implemented when an organization chooses one to protect their data.
- One way this is done is using OpenSSL, which is an open-source command line tool that can be used to generate public and private keys. OpenSSL is commonly used by computers to verify digital certificates that are exchanged as part of public key infrastructure.

### 2.02.04 - Obscurity is not security

- In the world of cryptography, a cipher must be proven to be unbreakable before claiming that it is secure. 
- According to [Kerchoff’s principle](https://en.wikipedia.org/wiki/Kerckhoffs%27s_principle), cryptography should be designed in such a way that all the details of an algorithm—except for the private key—should be knowable without sacrificing its security.

***NOTE***: 
	- A cryptographic system should not be considered secure if it requires secrecy around how it works.
	- The `tr` command translates text from one set of characters to another, using a mapping. The first parameter to the `tr` command represents the input set of characters, and the second represents the output set of characters. Hence, if you provide parameters “*abcd*” and “*pqrs*”, and the input string to the tr command is “*ac*”, the output string will be “*pr*".

---

## 2.03 - Hashing <a name="203---hashing"></a>

- **Hash Function** - an algorithm that produces a code that can't be decrypted.
- **Non-repudiation** - the concept that the authenticity of information can't be denied.

![[hash-functions.png]]

### 2.03.01 - MD5

- **MD5**(***Message Digest 5***)
- Professor Ronald Rivest of the Massachusetts Institute of Technology (MIT) developed MD5 in the early 1990s as a way to verify that a file sent over a network matched its source file.
- works by converting data into a 128-bit value.
- in a hash table, bits appear as a string of 32 characters. Altering anything in the source file generates an entirely new hash value.
- the longer the hash value, the more secure it is.

### 2.03.02 - Hash collisions

- One of the flaws in all hash functions. 
- Hash algorithms map any input, regardless of its length, into a fixed-size value of letters and numbers. 
- Although there are an infinite amount of possible inputs, there’s only a finite set of available output.
- MD5 values are limited to 32 characters in length. Due to the limited output size, the algorithm is considered to be vulnerable to hash collision, an instance when different inputs produce the same hash value. 
- Because hashes are used for authentication, a hash collision is similar to copying someone’s identity. Attackers can carry out collision attacks to fraudulently impersonate authentic data.

### 2.03.03 - Next-generation hashing

- To avoid the risk of hash collisions, functions that generated longer values were needed. 
- MD5's shortcomings gave way to a new group of functions known as the **SHA**(***Secure Hashing Algorithms***).
- The **NIST**(***National Institute of Standards and Technology***) approves each of these algorithms. 
- Numbers besides each SHA function indicate the size of its hash value in bits. Except for SHA-1, which produces a 160-bit digest, these algorithms are considered to be collision-resistant. However, that doesn’t make them invulnerable to other exploits.
- Five functions make up the SHA family of algorithms:
	1. SHA-1
	2. SHA-224
	3. SHA-256
	4. SHA-384
	5. SHA-512

### 2.03.04 - Rainbow Tables

- A rainbow table is a file of pre-generated hash values and their associated plaintext. 
- They’re like dictionaries of weak passwords. 
- Attackers capable of obtaining an organization’s password database can use a rainbow table to compare them against all possible values.
- Functions with larger digests are less vulnerable to collision and rainbow table attacks.

### 2.03.05 - Salting 

- Salting is an additional safeguard that's used to strengthen hash functions. 
- A salt is a random string of characters that's added to data before it's hashed. 
- The additional characters produce a more unique hash value, making salted data resilient to rainbow table attacks.
- Similar to hash values, the longer and more complex a salt is, the harder it is to crack.
- For example, a database containing passwords might have several hashed entries for the password "password." If those passwords were all salted, each entry would be completely different. That means an attacker using a rainbow table would be unable to find matching values for "password" in the database.

![img](assets/salting.png)

---


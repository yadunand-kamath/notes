
## Data Security

- **Data Security Lifecycle**: Create -> Store -> Use -> Share -> Archive -> Destroy

- **Hashing** puts data through a hash function or algorithm to create an alphanumeric set of figures, or a digest. No matter how long the input is, the hash digest will be the same number of characters.

- **Symmetric Encryption** uses the same key in both the encryption and the decryption processes. It could be said that the decryption process is a mirror image of the encryption process.  This means that the two parties communicating need to share knowledge of the same key. Sending the key through a different channel (band) than the encrypted message is called **out-of-band key distribution**. Scalability issue - The number of keys needed grows quickly as the number of different users or groups increases. However, symmetric encryption has the least amount of processing overhead.

- **Asymmetric Encryption** uses one key to encrypt and a different key to decrypt the input plaintext. It solves the problem of scalability. However, asymmetric cryptography is extremely slow compared with its symmetric counterpart.

- **PKI** (***Public Key Infrastructure***) - One half of the key pair is kept secret; only the key holder knows that key - **private key**; the other half of the key pair can be given freely to anyone who wants a copy - **public key**.


---

## Event Logging

- **Ingress Monitoring** refers to surveillance and assessment of all inbound communications traffic and access attempts. Devices used for monitoring include: firewalls, gateways, SIEM solutions, IDS/IPS tools.
- **Egress Monitoring** is used to regulate data leaving the organization’s IT environment. For **DLP** (***Data Loss Prevention***), following tools are used: FTP, email, copy to portable media, APIs, posting to websites.
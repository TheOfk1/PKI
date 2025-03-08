## Encryption
- What is encryption? (an algorithm used to transform data so that only authorized parties may be able to see it)
- What are the uses of encryption? (protect data from being stolen or changed)
- How does encryption protect the data? Why can't I just reverse the algorithm? (There is a use of a secret key that is known only by select parties)
- If I wanted to break a strong encryption, What would I need to do? (brute force the key)
- What are some examples of encryptions? Which one is the one we prefer using today? What reasons are there for it being strong? (AES, DES, RC4. AES is currently considered the standard, their strength comes from their key size and the amount of cycles)
- What is the disadvantage for to large a key size? What about the number of cycles? (slower)
- Why is the XOR cipher weak? (only one plaintext to break + you can guess parts of the key at a time)
- What are some real life scenarios where you use encryption? (Whatsapp, browsing, Ubbi dubbi)
- What types of encryption are there? (Symmetric, A-Symmetric)
- Compare symmetric and a-symmetric encryption
	- Keys used
	- Speed
	- Security
	- Key distribution
	- Uses (encrypt data in database or file, digital signatures)
	- Algorithms (RSA, ECC, AES, DES, RC4)
- How is symmetric encryption used with a-symmetric encryption? (agree on secret)
- What is bit strength? 
- What mathematical principal does A-Symmetric encryption rely on? (integer factorization)
## Hash
- What is a hashing function? (fixed size output, deterministic)
- What are its uses? (password storage, data signature, checksum, key derivation, blockchains)
- What important properties does it have? (one way, collision resistant, uniform, avalanche)
- What does it mean if there is a hash collision? Can two different passwords work?
- What are some examples of hashing algorithms? (SHA256, MD4)
- Lets say I found the password hash for a user, how would I go about breaking it? What mitigates this threat? (rainbow table, salt)
- What is the difference between a hash function and an encryption? (use cases, hash is irreversible)
- <font color = "Blue">Not Needed</font> What is the difference between a hash function and an HMAC? (HMAC uses a secret key aswell)
#### Digital signature
- What is a digital signature? (combination of hash and encryption for integrity, authenticity. Equivalent of actual signatures)
- Examples (documents, certificates, software, block chains)
## Diffie Hellman
- What if there is an attacker?
- Should we event do this?
## RSA
- Should we even do this?
## TLS
[TLS](<Transport Layer Security>)
- What is it? (protocol used to transfer data securely)
- How many versions are there? What came before it?
- <font color="Blue">Not Needed</font> What is the difference between TLS 1.2 and TLS 1.1?
- Explain the TLS protocol in detail
- What is a cipher suite? What does each part mean? ![tls-cipher-stuite.png](./Assets/tls-cipher-suite.png)
- Why do you need a client and server random? (protect from replay attacks)
- What is elliptic curve cryptography? (same principals, harder to reverse)
- What is mutual TLS? What does it add to the current protocol?
- <font color="Red">Bonus</font> What are the protocol extensions in the client hello?
- If the server has a private / public pair, then why even use TLS? Why not just use the servers public key?
## Rivest Shamir Adleman
- What does the abbreviation stand for?
- How does it work?
## Diffie Hellmen
- What is it used for?
- How does it work?
- What stops man in the middle attacks?
## Public Key Infrastructure
- What is a PKI? (entities, roles, policies and software to allow the use of certificates and public key cryptography)
- How does a PKI infrastructure help prevent man in the middle attacks?
- Who are the entities of a PKI infrastructure? (registration authority, certification authority, certificate distribution point, OSCP endpoint) ![pki-entities](./Assets/pki-entities.png)
## Certificates
- What is it? (electronic document used to prove identity)
- What are some examples of certificates uses? (email, digital signature, TLS)
- What can be inside of a SAN?
- Where are certificates stored in a windows machine? What types of store are there? (certificate store, user, machine)
- How can you distribute certificates? (GPO)
- What are wildcard certificates? (uses asterisk in domain name)
- How can you save a certificate?
	- CSR - Certificate signing request
	- CRL - Certificate revocation list
	- CERT, CRT, CER, DER - PEM or DER encoded certificate
	- PKCS12, PFX, P12 - Holds certificates with private key, protected by password.
	- PEM - Encoding of certificates, may have private key
	- KEY - Holds PEM encoded private key
- What are certificate templates? (predefined structure used to create certificates)
- What are the certificate validation types? How do you know the extended verification of a certificate? (based on the certificate policies extension)
	- Domain validation - CA confirms ownership of the domain name
	- Organization validation - CA also confirms the business is registered
	- Enterprise validation - 9 rigorous steps of validation - was previously given a green highlight in a browser
- If the certificate is sent during the TLS handshake, what's stopping me from stealing it? What happens if I do manage to find the private key?
#### Chain of trust
- What's stopping me from issuing a certificate to impersonate an entity?
- What is a chain of trust?
- What are intermediate CAs? What are root CAs? Who signs the certificates of each one?
- Why is there both intermediate and root CAs?
- How can I trust root CAs?
## Extra
- What is the zero trust approach?
- What is a zero knowledge proof?
- Quantum computers
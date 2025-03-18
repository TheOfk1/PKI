## Encryption
- What is encryption? (an algorithm used to transform data so that only authorized parties may be able to see it)
- What are the uses of encryption? (protect data from being stolen or changed, 2 examples)
	- What are some real life scenarios where you use encryption? (Whatsapp, browsing, Ubbi dubbi)
- How does encryption protect data? Why can't I just reverse the algorithm? (There is a use of a secret key that is known only by select parties)
- As an attacker, What would I want to gain access to?
- When a strong encryption algorithm is used, what would we need to do to find the secret key?
- What are some examples of encryptions? Which one is the one we prefer using today? What reasons are there for it being strong? (AES, DES, RC4. AES is currently considered the standard, their strength comes from their key size and the amount of cycles)
	- What is the difference between AES128 and AES256, which is stronger? Why?
	- What is the difference between DES and 3DES, which is stronger? Why?
- $\color{Blue}\text{Not Needed}$ What is bit strength? (The magnitude of actions needed to break the encryption)
- What is the disadvantage for too large a key size? What about the number of cycles? (slower)
- $\color{Red}\text{Bonus}$ Why is the XOR cipher weak? (only one plaintext to break + you can guess parts of the key at a time)
- What types of encryption are there? (Symmetric, A-Symmetric)
- Compare Symmetric and A-Symmetric encryption
	- Keys used
	- Speed
	- Key distribution
	- Uses (encrypt data in database or file, digital signatures)
	- Examples (Kerberos, LDAP/TLS, What's App)
	- Algorithms (RSA, ECC, AES, DES, RC4)
	- $\color{Red}\text{Bonus}$ Security
- What is the problem with Symmetric encryption (regarding the shared secret)? How can you solve that problem?
- $\color{Blue}\text{Not Needed}$ What mathematical principal does A-Symmetric encryption rely on? (integer factorization)
## Hash
- What is a hashing function? (fixed size output, deterministic)
- What are its uses? (password storage, data signature, checksum, key derivation, blockchains)
- What important properties does it have? What is the difference between a hash function and encryption? (one way, collision resistant, uniform, avalanche. uses, irreversible)
- What are some examples of hashing algorithms? (SHA256, MD4)
- What does it mean if there is a hash collision? Can two different passwords work?
- Lets say we found the password hash for a user, how would we find the password from the hash? What mitigates this threat? (rainbow table, salt)
- $\color{blue}\text{Not Needed}$ What is the difference between a hash function and an HMAC? (HMAC uses a secret key as well)
#### Digital signature
- What is a digital signature? Why is it named so? (combination of hash and encryption for integrity, authenticity. Equivalent of actual signatures)
- How does it relate to certificates?
- Examples (documents, certificates, software, email)
## Diffie Hellman
- How does it work?
- What attack is there on Diffie Hellman? (MiTM)
- $\color{Red}\text{Bonus}$ What is the discrete logarithm problem?
## RSA
- How does it work?
- What is the abbreviation stand for?
## TLS
[TLS](<Transport Layer Security>)
- What is it? (protocol used to transfer data securely)
- How many versions are there? What came before it? (SSL 3.0, TLS 1.3)
- $\color{blue}\text{Not Needed}$ What is the difference between TLS 1.3 and TLS 1.2 and TLS 1.1?
- Explain the TLS protocol in detail
- What is a cipher suite? What does each part mean? ![tls-cipher-stuite.png](./Assets/tls-cipher-suite.png)
- Why do you need a client and server random? (protect from replay attacks)
- $\color{Blue}\text{No Needed}$ What is elliptic curve cryptography? (same principals, harder to reverse)
- What is mutual TLS? What does it add to the current protocol?
- $\color{red}\text{Bonus:}$ What are the protocol extensions in the client hello?
- If the server has a private / public pair, then why even use TLS? Why not just use the servers public key? (Certificate fields)
## Public Key Infrastructure
- What is a PKI? (entities, roles, policies and software to allow the use of certificates and public key cryptography)
- How does a PKI infrastructure help prevent man in the middle attacks?
- Who are the entities of a PKI infrastructure? (registration authority, certification authority, certificate distribution point, OSCP endpoint) ![pki-entities](./Assets/pki-entities.png)
## Certificates
- What is it? (electronic document used to prove identity)
- What are some examples of certificates uses? (email, digital signature, TLS)
- Where are certificates stored in a windows machine? What types of store are there? (certificate store, user, machine)
- How can you view machine certificates, How can you view user certificates?
- Say you created a self signed certificate, how can you make it so that your computer trusts it? What permissions are required to do so?
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
- If the certificate is sent during the TLS handshake, what's stopping me from stealing it? What doesn't the certificate contain? Where is the private key saved? What happens if someone finds it?
#### Certificate Revocation List
- What is a CRL? Who publishes it?
- Why would you want to revoke certificate? (it is compromised)
- How can I know a CRL hasn't been changed? (It is signed)
- Where can we see the URL for the CRL? (CDP)
###### Online Certificate Status Protocol
- What is the OCSP protocol? (over http, gets status of certificate)
- $\color{blue}\text{Not Needed}$ Where is the OCSP URI saved? (Authority Information Access)
- What OCSP stapling? (Server gets OCSP response with a timestamp and staples it to the message sent back to the client)
	- What is the advantage of OCSP over a CRL?
- Which would you like to use, OCSP or CRLs? (CRLs don't expose what sites client access, they provide less workload, and OCSP is over plain http)
- $\color{blue}\text{Not Needed}$ Is OCSP still supported?
#### Chain of trust
- What's stopping me from issuing a certificate to impersonate an entity?
- What is a chain of trust?
- What are intermediate CAs? What are root CAs? Who signs the certificates of each one?
- Why are there both intermediate and root CAs?
- How can I trust root CAs?
#### X.509 Extensions
- What is the X.509 format? (set of extensions for certificates, CSR's, CRL's)
- What is a serial number? Is it unique? What is a thumbprint? What's the difference?
- What is the thumbprint used for? What other name for it is there? (Identifying the certificate, fingerprint)
- What is the signature? (the digital signature method and hash used)
- What is a CDP? (CRL distribution point, the endpoint to get the CRL)
- What is the not before and not after fields? Why do they exist?
- What is the Issuer and subject fields? How do they look? (look like a common name)
	- What is the subject field used for? Is there another field for that purpose? (verify name of the service accessed, the SAN can also be useful)
- What is the SAN field? What can be a part of it? (Email, DNS, IP, URI)
	- What is the SAN field used for? (verify service)
	- What is the difference between the subject field and the SAN? (SAN can hold multiple fields)
- What is the key usage and extended key usage fields? Why do they exist? (minimize damage if certificate is compromised)
	- Give some examples of key usages
		- digital signature
		- data encipherment
		- certificate signing
		- key agreement
	- Give some examples of extended key usages
		- server authentication
		- client authentication
		- code signing
		- email protection
- What is the relationship between key usages and EKU? ![key-usage-extended](./Assets/eku.png)
- Can you start a TLS session with a server that doesn't have the server authentication EKU?
- What is the difference between a signature algorithm and a signature hash algorithm?
- $\color{blue}\text{Not Needed}$ How are key usages and extended key usages identified? (OID)
- $\color{blue}\text{Not Needed}$ What is the relationship between key usages and extended key usages? Which one is applied?
## OpenSSL
- What is OpenSSL? Give some examples of things it can do
	- It is an open source cryptographic library. It can provide TLS implementation, encryption algorithm and hash implementations, key generation, creating certificates and more
## TLS attacks
- What is SSL stripping? ![SSL stripping](./Assets/ssl-stripping-attack.png)
- What is heart bleed?
- What is a MiTM attack?
## Extra
- What is the zero trust approach?
- What is a zero knowledge proof?
- Quantum computers
- What component of windows handles secure communications? (SSPI's schannel)
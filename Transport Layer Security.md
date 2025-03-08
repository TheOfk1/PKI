[TLS bit by bit](<https://tls12.xargs.org/>)

TLS 1.0 is the minor version for Secure Socket Layer (SSL), and TLS has 4 versions: TLS 1.0 - TLS 1.3
## Messages
#### Client Hello
- Protocol version
- Client random - helps protect against replay
- Cipher suites
- Session ID - optional
- Compression methods
- Extensions
	- Server Name
	- Status Request
	- Signature Algorithms
#### Server Hello
- Protocol version
- Server random
- Cipher suite
- Session ID - optional
- Compression method
- Extensions
#### Server Certificate
- Certificate
#### Server key exchange
The server calculates a private / public key pair using the key exchange algorithm specified in the cipher suite.

It then sends the following:
- Key exchange protocol information
- Public key (Might be from Elliptic Curve Diffie Hellman)
- Signature - encryption of hash(client random, server random, curve info, public key) with servers private key of the certificate.
#### Server hello done
Server is done with its half of the handshake
#### Client key exchange
Same as server key exchange.
#### Client key calculations
The client calculates a PreMasterSecret based on the key exchange algorithm and:
- Client private key
- Servers public key

The client then calculates the encryption keys using the hash algorithm of the cipher suite and the client random, server random and PreMasterSecret.
#### Client change cipher spec
Clients next message will be encrypted
#### Client handshake finished
HMAC of all handshake messages so that it can be verified that the handshake hasn't been tampered with.
#### Server key calculations
Same as client
#### Server change cipher spec
Same as client
#### Server handshake finished
Calculates HMAC of handshake and verifies it against the clients handshake finished.
#### Data exchange
data exchange as necessary by the application protocol.
#### Client close notify
Client closes connection
## About client and server random
Without the client and server random in combination with weak key exchange algorithms the pre-master secret generation can be predicted.

You will then be able to figure out the pre-master secret using a precomputed table of pre-master secrets and the data sent in the TLS handshake.

Some examples of it are:
- Debian OpenSSL Vulnerability (CVE-2008-0166)
- Logjam attack (CVE-2015-4000)
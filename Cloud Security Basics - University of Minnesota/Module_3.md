# Step 5: Remote Administration

- **Separation of duties**: Site management and system administration should be distinct roles
- **Privileged access control**: Ensure only authorized personnel can perform administrative actions
- **Integrity protection**: Prevent unauthorised modifications (accidental or intentional) to administrative commands and results
- **Confidentiality**: Protect administrative secrets from unauthorised disclosure

## Cloud Deployment Model

- The deployment model remains **off-site-private**, similar to Step 4
- Administrative operations are moved to separate Internet sites, outside the server's trust boundary
- This increases risks, particularly **credential sniffing**
- **Encryption prevents credential sniffing**:
  - Unprotected passwords transmitted online can be intercepted
  - Encryption scrambles data, making it unreadable to attackers
  - Only the intended recipient can decrypt and access the original data
- **Ciphers and Encryption Mechanisms**:
  - **Plaintext**: Unprotected, readable data
  - **Ciphertext**: Encrypted data that is safe outside the trust boundary
  - **AES (Advanced Encryption Standard)**: A well-established encryption standard
  - Cipher security relies on **strong, well-studied cryptographic methods**
- **Encryption Challenge**: 
  - Encryption replaces the problem of securing plaintext with the problem of securely sharing encryption keys

## Secret Sharing with Public-Key Cryptography

- **Problem**: Securely sharing encryption keys over the Internet without prior arrangement
- **Solution**: Public-key cryptography (asymmetric encryption) enables secure key exchange

### Public-Key Cryptography Process
1. Each party generates a **public-private key pair**
2. The **public key** is shared openly
3. The **private key** is kept secret
4. The **shared secret** is computed using:
    - **Client's private key + Server's public key**
    - **Server's private key + Client's public key**
5. Attackers intercepting the public key cannot reconstruct the shared secret

### Key Exchange Mechanisms
- **Diffie-Hellman (DH)**: Traditional method for secret key exchange
- **Elliptic Curve Cryptography (ECC)**: More efficient but not as thoroughly studied as DH

## Transport Layer Security (TLS) for Secure Communication

- **TLS (formerly SSL)** secures Internet communications from eavesdropping and interception
- **Uses Cases in Remote Administration**:
  - Protecting administrative credentials and commands
  - Securing transmission of authentication secrets (e.g., off-site backups)
  
- **TLS Handshake Process**:
  1. **Key Generation**: Both client and server create public-private key pairs
  2. **Public Key Exchange**:
     - Client sends its **public key** to the server, requesting a TLS connection
     - Server generates its **public-private key pair**
     - Server sends its **public key** to the client
  3. **Shared Secret Computation**:
     - Each party combines its **private key** with the other party’s **public key** to generate a **shared secret**
  4. **Secure Session Establishment**:
     - Shared secret is used to derive **encryption keys**
     - Separate keys are created for client messages and server messages
     - Messages are encrypted and securely exchanged

# Quiz: Public Key Exchange and TLS

## Question 1

Why is credential sniffing such a problem on the public internet? Select all that apply. 

- **Traditional protocols transmit credentials in plaintext**
- Client computers don't hash passwords before sending them across the internet
- Many sites use HTTPS instead of HTTP
- **Internet routing may transmit a packet containing credentials through untrustworthy hosts, networks, and routers**

*Note: Credential sniffing was not judged a risk when internet protocols were first developed in the 1980s. The server's verifier software should receive the plaintext password. HTTPS provides encryption and HTTP does not. Routing is highly persistent and does not always take into account the trustworthiness of the hosts or networks on a route.*

## Question 2

Is it easier to protect passwords or cryptographic keys when sharing them on the internet?

- Passwords are easier to protect because they are in text format
- Secret keys are easier to protect because they are in raw binary format
- **Both are equally difficult**

## Question 3

Which keys are kept secret if a client and server use public-key sharing to construct a shared secret?

- Server's public key
- **Server's private key**
- Client's public key
- **Client's private key**

*Note: Public keys are always meant to be shared in public-key cryptography. Private keys are always meant to be kept secret by a single entity.*

## Question 4

How do we construct a shared secret using public-private key pairs?

- The client combines their own private key with the server's private key, and vice versa
- **The client combines their own private key with the server's public key, and vice versa**
- The client combines their own public key with the server's private key, and vice versa
- The client combines their own public key with the server's public key, and vice versa

## Question 5

What type of cryptography does TLS typically use to encrypt data shared between the client and server?

- RSA
- Diffie-Hellman
- **AES**
- Elliptic curve

*Note: AES was designed to encrypt large amounts of data.*


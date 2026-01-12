# Cryptography

Cryptography is a branch of mathematics (from Greek: "secret writing"). It includes techniques to:
- Prove knowledge of a secret without revealing it (digital signatures)
- Prove authenticity and integrity of data (hashes)
- Provide other mathematical tools that form the foundation of blockchain systems like Ethereum

These cryptographic proofs are critical to Ethereum's operation and extensively used in Ethereum applications.

## Keys and Addresses

### Private Keys and Ownership

- Ownership of ether by **EOAs (Externally Owned Accounts)** is established through:
  - Digital private keys
  - Ethereum addresses
  - Digital signatures

- A private key uniquely determines a single Ethereum address (account)
- **Private keys are never transmitted or stored on Ethereum** - only account addresses and digital signatures are transmitted and stored on-chain

### Ethereum Addresses

- An Ethereum address functions like beneficiary account details in a bank transfer
- For EOAs, addresses are generated from the public key portion of a key pair
- **Address generation process:**
  1. Public key is derived from private key using elliptic curve cryptography
  2. Keccak-256 hash is applied to the public key
  3. Take the last 20 bytes (40 hex characters) of the hash
  4. Prepend with "0x" prefix
  5. Apply checksum encoding (EIP-55) for mixed-case representation

- **Address types:**
  - **EOA addresses:** Generated from public keys (controlled by private keys)
  - **Contract addresses:** Generated deterministically from creator's address and nonce

## Public Key Cryptography (PKC)

PKC (also called asymmetric cryptography) is a core part of modern information security. The key exchange protocol, first published in the 1970s by Martin Hellman, Whitfield Diffie, and Ralph Merkle, sparked the first major wave of public interest in cryptography.

### Mathematical Foundations

Keys are based on mathematical functions with a special property: **easy to calculate forward, hard to calculate backward (inverse)**. This enables:
- Creation of digital secrets
- Unforgeable digital signatures
- Security based on mathematical laws

### Cryptographic Primitives

**Prime Factorization:**
- Multiplying two large prime numbers is trivial
- Finding prime factors of their product is computationally infeasible

**Trapdoor Functions:**
- Functions that are difficult to invert unless given secret information
- The secret allows easy reversal of the function

**Elliptic Curve Cryptography (ECC):**
- Commonly used in modern computer systems
- Basis for private keys and digital signatures in almost all blockchains
- Ethereum uses the **secp256k1** curve (same as Bitcoin)

**Discrete Logarithm Problem:**
- In elliptic curve arithmetic, multiplication modulo a prime is simple
- Division (the inverse) is practically impossible without the private key

### Ethereum's Use of PKC

Ethereum uses PKC to create public–private key pairs that represent an Ethereum account:
- **Public key → Address:** Publicly accessible account handle
- **Private key:** Provides private control over:
  - Access to ether in the account
  - Authentication needed when using smart contracts

## Digital Signatures

### ECDSA (Elliptic Curve Digital Signature Algorithm)

- Ethereum uses **ECDSA** with the **secp256k1** curve for digital signatures
- Process:
  1. Private key signs a message (transaction)
  2. Signature proves ownership without revealing the private key
  3. Anyone can verify the signature using the public key/address

### Signature Components

- **r, s values:** Mathematical components of the signature
- **v value:** Recovery identifier (determines which public key created the signature)
- Together, (r, s, v) allow anyone to verify the signature and recover the signer's public key

## Hash Functions

### Keccak-256

- Ethereum uses **Keccak-256** (part of SHA-3 family) as its hash function
- Produces 256-bit (32-byte) output
- Used for:
  - Generating addresses from public keys
  - Creating transaction hashes
  - Block hashing
  - State tree construction

### Properties of Cryptographic Hashes

- **Deterministic:** Same input always produces same output
- **Fast to compute:** Hash calculation is efficient
- **One-way:** Cannot reverse hash to get original input
- **Avalanche effect:** Small input changes produce completely different outputs
- **Collision resistant:** Practically impossible to find two inputs with same hash

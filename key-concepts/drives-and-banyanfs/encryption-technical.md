# 🔐 Encryption (technical)

BanyanFS uses end-to-end encryption (E2EE) so that only users have access to their data. Each unique actor has a key pair for the NIST P-384 elliptic curve. The private key can be used to sign changes and to encrypt or decrypt the filesystem, while the public key can be used to verify signatures.

The private key remains with the user and the public key is stored in the root of the filesystem itself to enable [#asynchronous-diffie-hellman-key-exchange](encryption-technical.md#asynchronous-diffie-hellman-key-exchange "mention"). Each node in the filesystem is the root of its own filesystem which enables an [#encapsulated-encryption](encryption-technical.md#encapsulated-encryption "mention") approach. We use XChaCha20Poly1305 to do encryption of the files themselves.

See [https://gist.github.com/sstelfox/c6b6cfe998b6fa5377aebca3313405d5](https://gist.github.com/sstelfox/c6b6cfe998b6fa5377aebca3313405d5) for a draft of the spec. It is probably out of date, but you can get an idea...

### Asynchronous Diffie-Hellman Key Exchange

Because users may wish to share files with others who are not actively online, BanyanFS uses an asynchronous approach to key exchange by encoding public keys in the format itself. This proceeds similarly to a regular Diffie-Hellman key exchange, except that an intermediary key is generated and stored in the filesystem to later be used to complete the exchange. When the exchange is completed, a user takes this intermediary key and uses it to generate a permanent key, which is then able to decrypt the filesystem.

### Hierarchical Encryption

TODO: go over hierarchical encryption situation

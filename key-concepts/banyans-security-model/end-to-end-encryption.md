# 🔐 End-to-end Encryption

All files that are uploaded to BanyanFS are automatically end-to-end encrypted (E2EE) by default. This goes above and beyond what other centralized and decentralized storage providers offer and reinforces our ethos that users should be the only ones who can access and control their data. No one (not even Banyan or SPs) will be able to access user files.&#x20;

We believe that E2EE is the best solution for security in distributed contexts. But using encryption in distributed systems makes collaboration technically challenging. BanyanFS uses an asynchronous [Diffie-Hellman key exchange](https://en.wikipedia.org/wiki/Diffie%E2%80%93Hellman\_key\_exchange) algorithm with hierarchically-organized keys so that authorized users can share granular access to the filesystem with anyone at any time. This means that BanyanFS lets you share limited or full access to individual files and folders without needing to give access to the whole filesystem.

For more technical details, check this out: [encryption-technical.md](../drives-and-banyanfs/encryption-technical.md "mention")

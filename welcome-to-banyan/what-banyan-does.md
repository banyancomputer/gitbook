---
description: A technical explainer from client to cloud and back.
---

# 💡 What Banyan Does

### Pack and encrypt filesystems with their histories

Banyan starts with files. We take a filesystem locally on your machine (in the case of the CLI) or an empty filesystem initialized to take files (for the SDK and webapp) and put it into a content-addressed, versioned, audit-logged, and encrypted format, called BanyanFS. You can read more about it here: [drives-and-banyanfs](../key-concepts/drives-and-banyanfs/ "mention").

What does this mean? A content-addressed filesystem (CAF) is a filesystem that stores data based on its content rather than its location or filename. Each piece of data is given a unique identifier based on its content allowing the user to easily retrieve data that corresponds with the identifier. [UnixFS](https://docs.ipfs.tech/concepts/file-systems/#unix-file-system-unixfs) and [WNFS](https://github.com/wnfs-wg/rs-wnfs) are two well-known examples of a CAF.\
\
The unique identifier is usually in the form of a cryptographic hash. Unlike traditional storage systems, a CAF is defined by these identifiers vs. directories and filenames. Journaling records any modifications to a file (creations and deletions). Journaling helps ensure file consistency, especially in the case of unexpected disruptions (i.e. power outage or system failure). In BanyanFS, the journal itself is included in the root hash. This ensures the integrity of the entire filesystem (including journal) can be verified using a single cryptographic hash.

BanyanFS is configured to permit versioning and audit logging. These features help users maintain multiple iterations of a file or dataset over time. History tracking, rollbacks, and branching and merging, are all key aspects of versioning. Audit logging helps Banyan users maintain the security and integrity of data storage, especially in regions&#x20;

What is versioning/audit logging:&#x20;



TODO and link [journaling-versioning.md](../key-concepts/drives-and-banyanfs/journaling-versioning.md "mention")

Read more about our encryption here: TODO link e2e encryption [journaling-versioning.md](../key-concepts/drives-and-banyanfs/journaling-versioning.md "mention")

### Track filesystem root hashes, enforce write permissions

We track the most recent root hash and manifest of blocks to keep live in&#x20;

### Meter data and bandwidth usage, bill for it using Stripe

TODO

### Enforce block lifecycling for the filesystem

TODO

### Route data directly to monitored and contracted storage providers with capacity

TODO

### Enforce read permissions: Kerberos-style permissioned retrievals using UCAN

TODO

### Ensure data is retrievable on-demand with low latency

TODO

### Replicate data, manage failover, self-heal

TODO

### Optionally: serve data over S3 and IPFS

S3 is coming very soon. See [s3-compatibility-layer.md](../getting-started/s3-compatibility-layer.md "mention").

IPFS availability (for blocks, or for UnixFS-formatted files) is further out. If you would pay us for this and have a sizable amount of data, reach out [on our website](https://banyan.computer) (and we might prioritize this feature higher).

---
description: A technical explainer from client to cloud and back.
---

# 💡 What Banyan Does

### Pack and encrypt filesystems with their histories

Banyan starts with files. We take a filesystem locally on your machine (in the case of the CLI) or an empty filesystem initialized to take files (for the SDK and webapp) and put it into a content-addressed, versioned, audit-logged, and encrypted format, called BanyanFS. You can read more about it here: [drives-and-banyanfs](../key-concepts/drives-and-banyanfs/ "mention").

<details>

<summary>Track bucket root hashes in our infrastructure, enforce write permissions</summary>

We track the most recent root hash and manifest of blocks to keep around, live in our infrastructure in GCP. This is all that is stored or passes through GCP (assuming S3 mode is not on)- everything else is decentralized.

Banyan's infrastructure enforces permissions on writes to the bucket's root hash (i.e., updating latest state of the filesystem) and whether blocks affiliated with a given bucket can be added or deleted to SPs (i.e., you'll get billed for anything kept in or retrieved from your bucket).

</details>

<details>

<summary>Meter data and bandwidth usage, bill for it</summary>

We meter blocks stored over each month and how often they're retrieved from the SPs in our infrastructure. We bill users monthly using Stripe for their usage. We may eventually support crypto payments- let us know on [our website](https://banyan.computer) if you're interested.

</details>

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

### Optionally: serve data over S3

S3 is coming very soon. See [s3-compatibility-layer.md](../getting-started/s3-compatibility-layer.md "mention").

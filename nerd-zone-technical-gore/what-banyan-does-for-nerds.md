---
description: A technical explainer from client to cloud and back.
---

# 💡 What Banyan Does (for nerds)

<details>

<summary>Pack and encrypt filesystems with their histories</summary>

Banyan starts with files. We take a filesystem locally on your machine (in the case of the CLI) or an empty filesystem initialized to take files (for the SDK and webapp) and put it into a content-addressed, versioned, audit-logged, and encrypted format, called BanyanFS. You can read more about it here: [drives-and-banyanfs](../key-concepts/drives-and-banyanfs/ "mention").

</details>

<details>

<summary>Track filesystem root hashes, enforce write permissions</summary>

We track the most recent root hash and manifest of blocks to keep live in our infrastructure, on GCP. People who can write to a given drive are allowed to write blocks to the network (metered under that drive) and update the root hash in our infrastructure.

</details>

<details>

<summary>Meter data and bandwidth usage, bill for it using Stripe</summary>

Banyan keeps track of how much data you store and retrieve. We have integrated with Stripe and bill all users in USD.&#x20;

One day we might integrate crypto- let us know if you're interested so we can prioritize that feature [https://banyan.computer/contact](https://banyan.computer/contact)&#x20;

</details>

<details>

<summary>Enforce block lifecycling for the filesystem</summary>

Coming soon: we'll add lifecycling policies to the clients, making it so they can flag blocks for expiry.&#x20;

Lifecycle policies will look like "don't keep old versions that have been out of date for more than five years" or "only keep the past three versions".&#x20;

When our infrastructure gets an expiry request, we forward it to the appropriate storage providers to queue the data for deletion, and stop billing the customer for the storage as soon as it's removed from the network.&#x20;

Fulfillment of expiry requests is covered by our SLA. It may take longer to tombstone old data on cold storage than on hot storage.

</details>

<details>

<summary>Route data directly to monitored and contracted storage providers with capacity</summary>

We select where your data goes inside our infrastructure, based on a variety of factors including SP performance, available capacity, sealing capacity, and more.

Banyan SPs are vetted and monitored for performance and uptime. To make extra sure that your data is reliably live, we built our monitoring system to run alongside Filecoin's Boost and Lotus. It handles uptime and outage monitoring, ACLs, serving hot data, staging cold data for onboarding to Filecoin, and more.

Learn more here: [sp-relationships](../key-concepts/banyan-and-its-network/sp-relationships/ "mention").

</details>

<details>

<summary>Ensure data is retrievable on-demand with low latency</summary>

Your local copy of BanyanFS's headers knows which blocks are where, and which ones correspond to which file. When you open a file, it isn't necessarily stored locally. Your client will first get a signed grant from the Banyan servers to check the permissions, then it'll fetch it for you from a storage provider that has a copy. The SP is running our monitoring binary to check that you have access to that block and have paid for the bandwidth, which checks the signature on the grant and then sends you the data.

Items on the roadmap include better load-balancing to ensure that you get a fast download speed on the first try, or torrent-style download from multiple SPs to optimize throughput.

</details>

<details>

<summary>Enforce read permissions: Kerberos-style permissioned retrievals using UCAN</summary>

We do ACLs by having clients get a retrieval grant from our servers, which check who has read access to which drives. Then the client presents that to the SP, whose monitoring binary checks the signature, and then they send the data back.

We enforce the ACLs on the SP side (i.e., making sure they don't just hand your data out to people who fail the ACL check) using our binary and a contractual agreement between Banyan and the SP.

This is somewhat inspired by Kerberos. We use UCAN for our retrieval grants.

</details>

<details>

<summary>Replicate data, manage failover, self-heal</summary>

Banyan's self-healing properties ensure user data remains protected. If one or more SP experiences issues (i.e. network outage or hardware failure), a user's data is automatically replicated and stored on working SPs. Our infrastructure orchestrates failure detection and the data move. Learn more [here](../key-concepts/banyan-and-its-network/self-healing-storage.md).

</details>

<details>

<summary>Optionally: serve data over S3 and IPFS</summary>

Our S3 API is coming very soon. See [s3-compatibility-layer.md](../getting-started/s3-compatibility-layer.md "mention").

IPFS availability (for blocks, or for UnixFS-formatted files) is further out. If you would pay us for this and have a sizable amount of data, reach out [on our website](https://banyan.computer) (and we might prioritize this feature higher).

</details>

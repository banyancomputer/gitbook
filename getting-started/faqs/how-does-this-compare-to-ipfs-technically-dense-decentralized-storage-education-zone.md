# 😇 How does this compare to IPFS? (technically dense decentralized storage education zone)

{% hint style="info" %}
This page summarizes a conversation we have frequently with teams who are trying to build something based on decentralized storage. We hope it helps you understand your options. If you don't end up picking Banyan, at least we were helpful :relaxed:

If you're still confused about how to proceed, feel free to schedule a call. We're happy to trade you our expertise for your feedback.
{% endhint %}

[Jump to our favorite part: how does Banyan fit into the landscape?](how-does-this-compare-to-ipfs-technically-dense-decentralized-storage-education-zone.md#how-does-banyan-fit-into-all-this) :wink:

### What's IPFS?

IPFS is a Distributed Hash Table. This means you can look data up by its hash in a network of nodes. To access IPFS files through your browser, you use a (centralized) gateway. Some popular gateways are hosted by ipfs.io, Cloudflare, Infura, and Pinata. Gateways can censor, but you have optionality.

### Where are the incentives? How do I reliably store my data on there?

IPFS does not in itself provide any guarantees or incentives that the data in it will stick around. To get those guarantees, you use an IPFS pinning service. Pinata and Filebase (and many others!) run popular IPFS pinning services. This is (usually) a centralized entity that you pay to keep your IPFS-hosted data live and accessible.

Pinning services are great for small files, because they're usually pretty expensive per gigabyte of data (like, way way more than S3).

Pinning services, and IPFS in general, can occasionally take up to 50 seconds to resolve content and get it back to the user, especially if it's not cached on the gateway. This is because IPFS occasionally has to do lookups that traverse many nodes to find the data. This is very configuration and pinning-service dependent.

We get a lot of people who are frustrated with pinning services coming to us for help.&#x20;

### Is Filecoin IPFS' incentive layer?

Filecoin uses many of the same technologies as IPFS, but is not the same, and is not interoperable. Data on Filecoin does not imply data accessible on IPFS. Data on Filecoin has to be "sealed" to participate in consensus. Sealing and unsealing are a computationally intensive process (taking hours of GPU time per 32GB chunk), so Filecoin is not useful for hot data (...which is the use case that IPFS is intended for).&#x20;

Theoretically, you could advertise sealed Filecoin CIDs over IPFS and just take 3 hours to respond when they're requested. There are network indexer and retrieval projects in Filecoin-land that work on this, but _these are not something you want to use in prod_.

Sealed data is proven daily to exist and not be modified. You can learn more about Filecoin proofs [here](https://docs.filecoin.io/basics/the-blockchain/proofs) and [here](https://docs.filecoin.io/smart-contracts/advanced/aggregated-deal-making).&#x20;

### Retrieval Incentives?

You got me... Nobody who is new to decentralized storage would ever ask about this, but it's super important to understand.

There is a difference between incentivizing retrieval and incentivizing storage. You want your data to do two things when you store it- stick around (storage), and be accessible when you want it (uptime).&#x20;

Filecoin, Arweave, Storj, and all Data Availability layers that exist today all successfully and trustlessly incentivize the former.&#x20;

The latter is way more important, and (unfortunately) significantly more difficult, for reasons I'll eventually write a blog post on. Various teams are trying to solve this in ways that are various levels of decentralized, including Fleek, SkyNet, Saturn, Filecoin's retrieval pinning/other retrieval protocols.&#x20;

In my (Claudia's) opinion, none of these are anywhere near satisfactory or reliable yet, and there may never be a fully-satisfactory solution. Production applications should rely on a centralized trustworthy service to provide on-demand retrievals.

### Censorship?

There are two types of censorship- read censorship, and write censorship.&#x20;

Write censorship means someone is preventing you from putting the data onto the network and getting it covered by incentives. This is pretty easy to circumvent by simply going through a different provider. You can compare it to Ethereum block builder censorship, except it's a better situation because there is significantly more diversity in the market for most decentralized storage solutions.

Read censorship is trickier. It's related to the retrieval incentives problem above. If someone has the only copy of your data, they can refuse to send it to you. If there are a lot of copies, you may have better luck, but that's expensive.

### Permanent storage? Pay-once-store-forever?

We strongly believe that permanent storage is not a sustainable business model, which for most storage users should be a serious concern (because if your storage provider goes out of business, there goes your data). Feel free to reach out if you want more information about this.

Arweave via Bundlr is a popular solution for this, and [Lighthouse](https://www.lighthouse.storage/) is a Filecoin-based solution.&#x20;

Banyan does not offer this and does not plan to, but we're friends with Lighthouse- if you want some aspects of Banyan and some aspects of Lighthouse, we can probably work something out for you.

### What about \_\_\_\_\_\_ centralized onboarder service?

They're probably very convenient and easy to integrate with.

On the other hand, they are probably _very_ expensive compared to web2 options, probably secretly use AWS or Cloudflare R2 on the backend, and probably don't do much with security controls or SLAs.

This may not be a concern for you! If so, it will be a fine solution.

### How does Banyan fit into all this?

Our hot layer can be used similarly to IPFS pinning services, but is distributed over various Filecoin SPs. We will be adding our (independent) storage proof protocol to it sometime this year. It is also secured by Banyan-maintained centralized controls to ensure data is both retrievable with low latency and reliably stored.

Regarding IPFS compatibility, two pieces are necessary. Gateway-compatible file formats, and broadcasting CIDs to the IPFS network. BanyanFS may soon add a UnixFS compatibility mode, which will make our data wallets able to store public files that can be served through an IPFS Gateway. Once that's done, we can just stand up a service that's running a small fragment of an IPFS node next to our hot layer nodes, and we're running Banyan on IPFS.

_**If you are interested in using Banyan with IPFS, reach out and encourage us to prioritize it on our roadmap... It's currently not a high priority.**_

Our cold layer is Filecoin with a retrieval/permissioning layer over top. This means you get daily proofs of storage if you store data on Banyan cold storage. We also use our centralized monitoring and controls to ensure things _stay_ on Filecoin and are properly renewed or re-replicated.

We have a product that does encryption, versioning, and sharing management, all in a decentralized manner (maintained by a data wallet, BanyanFS). This is unique in the industry.

We have retrieval controls, meaning nobody can download your data without permission. This is also unique in the industry. It's centralized right now, but is UCAN-based, and could be partially decentralized to use a threshold network.

If we censor you or fire you as a customer, you can get your data off Filecoin by contacting the miner it's stored on, provided they haven't deleted it. It will be protected by Filecoin incentives until the end of the Filecoin deal, so the miner will have its collateral slashed if they delete your data. The miner _can_ _theoretically_ refuse to send you your data, or demand you pay them for its retrieval, but you should be able to get a copy back.&#x20;

tl;dr: when Banyan censors you, the worst that happens is your storage degrades to just being Filecoin without any bells and whistles.

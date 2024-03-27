# ✅ Filecoin & Proofs of Storage

Banyan is a thick, utility-packed layer on top of the Filecoin network. Banyan leverages Filecoin's [Proofs-of-Storage](https://docs.filecoin.io/basics/what-is-filecoin/blockchain#proofs) mechanism for data verification and integrity when it comes to archival storage. Additionally, Banyan relies on Filecoin’s vast network of storage providers (SPs) to replicate and safely store user data.

* Cold storage: Users can easily back up and archive data onto Filecoin through Banyan's UI via Snapshots.&#x20;
* Hot storage: Banyan has built a hot storage layer that quickly handles retrievals and provides Proofs of Storage (coming soon).
* Monitoring: Banyan runs its own binary (monitoring system) for SPs alongside Filecoin’s boost and lotus to ensure uptime and replication.
* Recovery: Banyan can custody a users’ keys and offer them additional features like Amazon S3 and compute.

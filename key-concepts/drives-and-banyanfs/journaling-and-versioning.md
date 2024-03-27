# 📒 Journaling and Versioning

Unlike traditional filesystems which store state directly, BanyanFS represents its state using a signed and versioned journal of changes, and records the cryptographic signature of each edit to a filesystem. This provides history tracking, rollbacks, and branching and merging; and empowers users to maintain multiple iterations of a file or dataset over time while tracking who has made changes to ensure the security and integrity of their data.

### Journal-as-State

While traditional filesystems use journals as an addition to the data store to ensure file consistency, in BanyanFS the journal _is_  the data store. Specifically, BanyanFS uses operation-based conflict-free replicated data types (CRDTs) to represent state as a catalogue of changes on data which can be repeated or "replayed" to reproduce any filesystem state, past or present.

### Versioning and Time Travel

As discussed in [content-addressing.md](content-addressing.md "mention"), filesystem data is represented by a CID, which is a hash of the data. In BanyanFS, since data is represented by the journal, the CID of a filesystem is also the CID of its journal. Combined with signed edits described in [encryption-technical.md](encryption-technical.md "mention"), this means verifying a CID verifies the current state of the filesystem as well as all previous versions of that state. Moving to a previous state moves to a previous CID and thus version. History, rollbacks, and auditing are extensions of the same core functionality.

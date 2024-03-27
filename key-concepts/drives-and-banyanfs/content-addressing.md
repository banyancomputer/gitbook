# 🏡 Content Addressing

A content-addressed filesystem (CAF) is a filesystem that references data based on its content rather than its location or filename. Each piece of data is given a unique identifier based on its content allowing the user to easily retrieve data that corresponds with that content. [UnixFS](https://docs.ipfs.tech/concepts/file-systems/#unix-file-system-unixfs) and [WNFS](https://github.com/wnfs-wg/rs-wnfs) are two well-known examples of a CAF. BanyanFS, our data wallet and the core of our tech, is a new CAF we built for performance and security on our platform.

### CIDs

CAFs use content-addressed identifiers (CIDs) to find data instead of filenames and directories. In BanyanFS, a CID is in the form of a BLAKE3 cryptographic hash. Content-addressing ensures data integrity because the CID is a hash of the data's state at any given time. This dovetails with journaling to strengthen data integrity and allow rollback to previous versions of data.

### Journaling and Content Addressing

Because BanyanFS represents state using its journal, the CID of the filesystem at any given time is a hash of the journal state at that time. Each change changes the CID so that each CID and thus each state is uniquely recorded and verifiable. Moving between versions moves between CIDs. You can read more about how [journaling-and-versioning.md](journaling-and-versioning.md "mention") work in the dedicated section.

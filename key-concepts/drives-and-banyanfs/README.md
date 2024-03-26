# 📎 Drives and BanyanFS

## How BanyanFS works

BanyanFS builds on and refines prior art in distributed data storage to provide end-to-end encryption without sacrificing collaboration and user control. A BanyanFS file system consists of a segment containing metadata as well as a content payload with hierarchically-encrypted data sections so that file shares are secure and granular. It also uses a signed, versioned journal for audited editing and historical rollback. You can read more about those features in&#x20;

### Drives

A Drive is a representation of a single BanyanFS file system. It's associated with the data itself, not a physical device, and is usually backed by both a local copy and one or more remote copies. You can manage your Drives in our [web interface](https://data.banyan.computer/) where you can browse and modify your files, as well as from the command line using our [CLI app](https://github.com/banyancomputer/banyan-cli).

### Creating a Drive

You can create drives from our web interface. See more info here: [creating-a-drive.md](../../getting-started/web-client/creating-a-drive.md "mention")

### Organizing your Projects

We recommend that you approximately map one drive to one collaborative project or app. This is the use case we're designing for, at least. Personal in one, one per workplace team, etc.&#x20;

This may be subject to change as we keep working on the product :smile:

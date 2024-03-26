# 3️⃣ S3 Compatibility Layer

Enabling this feature breaks end-to-end encryption by necessity.

Read the [note](s3-compatibility-layer.md#security-note) below for more information.

Coming soon!

<details>

<summary>Security note/How it works</summary>

S3 functionality breaks end-to-end encryption. This is because we can't send you your files over HTTP without decrypting them first.&#x20;

To enable S3 for a drive, you'll issue Banyan an encryption key for the drive that you want to serve over S3. We will custody that in an isolated area of our infrastructure. (TODO: add guide for how to do this in the frontend)

When you make a request using S3, it routes to a separate service that Banyan runs. That service will retrieve your drive, open using the key you issued us, and decrypt the file as we stream it to you.

</details>

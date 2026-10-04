# DPF Camera releases

This public repository is the production distribution channel for approved DPF Camera application releases. Production appliances retrieve metadata and release assets over HTTPS without GitHub accounts, tokens, SSH keys or interactive authentication.

The private `jameswendt/dpf-camera` repository remains the authoritative engineering source repository. Its visibility is not changed by this distribution repository. Development work and unreleased source history belong there, not here.

## Permitted public content

- Signed stable metadata (`stable.json` and `stable.json.minisig`)
- Release manifests and signatures
- Public verification keys and checksums
- Immutable approved DPF Camera application release artifacts
- Public release notes

Application artifacts may contain the application source required to run the appliance; publishing an approved artifact does not publish private engineering history.

Never publish private signing keys, GitHub or device credentials, SSH keys, development branches, unreleased source history, internal logs, customer data or production secrets here.

## Release trust and scope

The stable pointer identifies the approved immutable release. A newer development build or a GitHub “latest” result is not production approval. Appliances must authenticate signed metadata and verify the exact artifact checksum before installation. Only public verification keys belong on appliances.

Application updates do not manage Debian packages, the kernel, firmware or unattended installation.

## Production signing identity

The owner-controlled production Minisign public key is published at
[`keys/dpf-camera-production.pub`](keys/dpf-camera-production.pub).

- Key ID: `D755331F7CEE4765` (identifier, not a fingerprint).
- Public-key file SHA-256: `c4eea7fd0e3fb2eacbc935b2eb662f6d0666ad443647b0f3781f1934fe8460df`.

Appliances pin this public key through a trusted installation. They must not
replace their trust anchor by downloading a key from this repository.

The pinned key verifies `stable.json.minisig`, which authenticates `stable.json`.
The pointer identifies and hashes an immutable release manifest. That manifest
has its own `manifest.json.minisig` and authenticates the release ZIP SHA-256,
version, build commit, minimum version and supported hardware. Unsigned metadata,
GitHub latest and unsigned checksums are never production approval.

The encrypted private key remains exclusively under the owner's control on the
owner's Mac, outside both repositories, release packages and appliance backups.
It is never copied to an appliance or distribution system.

## Release status

The owner-signed v0.16.5 application release and matching signed stable metadata
are published. Artifacts are available in the immutable `v0.16.5` GitHub Release;
manifest copies are under `releases/0.16.5/`. The offline bundle carries the same
signed metadata and exact inner artifact as online installation.

Fleet deployment acceptance is pending. Publication and signatures establish
approval of these bytes; they do not by themselves certify hardware validation
or designate the release PRODUCTION STABLE.

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

**v0.16.5 deployment blocked — October 4, 2026. Do not install this candidate.**

Controlled deployment stopped before activation because required backup validation
rejects a legitimate escaped systemd filename. The production fleet remains on
v0.16.4. v0.16.5 is **not PRODUCTION STABLE**.

The root stable pointer and signature have been withdrawn. Their original signed
bytes are retained under `releases/0.16.5/` for traceability, alongside the manifest.
The immutable GitHub Release artifacts and signatures remain unchanged; the
release is marked as a blocked prerelease. An archived signature is not a current
installation recommendation. The offline bundle is also affected by this defect.

No replacement stable metadata will be published until a corrected candidate has
completed validation and owner signing. Update checks may report that the stable
channel is unavailable while this correction is pending.

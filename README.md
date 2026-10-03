# DPF Camera releases

This public repository is the production distribution channel for approved DPF Camera application releases. Production appliances retrieve metadata and release assets over HTTPS without GitHub accounts, tokens, SSH keys or interactive authentication.

The private `jameswendt/dpf-camera` repository remains the authoritative engineering source repository. Its visibility is not changed by this distribution repository. Development work and unreleased source history belong there, not here.

## Permitted public content

- Signed stable metadata (`stable.json` and `stable.json.sig`)
- Release manifests and signatures
- Public verification keys and checksums
- Immutable approved DPF Camera application release artifacts
- Public release notes

Application artifacts may contain the application source required to run the appliance; publishing an approved artifact does not publish private engineering history.

Never publish private signing keys, GitHub or device credentials, SSH keys, development branches, unreleased source history, internal logs, customer data or production secrets here.

## Release trust and scope

The stable pointer identifies the approved immutable release. A newer development build or a GitHub “latest” result is not production approval. Appliances must authenticate signed metadata and verify the exact artifact checksum before installation. Only public verification keys belong on appliances.

Application updates do not manage Debian packages, the kernel, firmware or unattended installation.

## Bootstrap status

This repository is initialized for the application update manager. Production signing and the signed stable publication workflow are not yet configured. No stable manifest or application artifact is published here yet. Repository creation alone does not establish a working or trusted update channel.

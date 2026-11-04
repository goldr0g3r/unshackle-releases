# Unshackle releases

Signed Android builds of **Unshackle**, an app that protects against porn through Device Owner
policies and a DNS filter. It doesn't use a VPN or an Accessibility service, so banking apps keep
working. Loosening a protection waits for a cool-down; tightening applies at once. There is
always a way out: a cool-down Full Release, or a recovery code held by a trusted person.

This repository only hosts release files. Each release has:

| File | What it is |
|---|---|
| `unshackle-vX.Y.Z.apk` | The signed app |
| `unshackle-vX.Y.Z.apk.sha256` | Its SHA-256 checksum |
| `update-manifest.json` | Version, checksum and signing certificate, read by the setup script and the app's updater |

## Verify before installing

Every release is signed with the same key. Its certificate SHA-256 digest is:

```
2b3c50f33d7a653dcac153d0c814eb672335bcb32fdc7f9fb72c6976fd57a6e1
```

```bash
sha256sum -c unshackle-vX.Y.Z.apk.sha256
```

```bash
apksigner verify --print-certs unshackle-vX.Y.Z.apk
```

Don't install an APK whose certificate digest differs, whoever sent it.

## Install

Unshackle has to become Device Owner once, over USB from a computer. It doesn't need root, an
unlocked bootloader, or a factory reset. Each release's notes give the exact steps. Installing
the APK straight on the phone works, but without Device Owner the app can't protect anything.

Pre-releases (`-rc.N`) are for testing on a phone you can set up over USB.

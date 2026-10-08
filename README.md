<p align="center">
  <img src="assets/brand/devi-readme-banner.svg" alt="DEVI" width="600">
</p>

<h1 align="center">DEVI Decrypt</h1>

<p align="center">
  Offline decryption of Apple and iCloud OpenPGP provider returns for digital forensic examiners.
</p>

<p align="center">
  <a href="https://deviops.app/tools/devi-decrypt/">Download</a> ·
  <a href="CHANGELOG.md">Changelog</a> ·
  <a href="SECURITY.md">Security</a> ·
  <a href="https://deviops.app">deviops.app</a>
</p>

---

DEVI Decrypt decrypts an Apple or iCloud provider return delivered as an OpenPGP file. It is for an examiner who already has the return and the key from the provider and needs to decrypt it on a Windows computer.

Apple and iCloud only. Other provider-return formats are not supported. DEVI Decrypt is an independent utility and is not affiliated with or endorsed by Apple Inc.

DEVI Decrypt is part of **DEVI**, a set of tools built by experienced digital forensic examiners for examiners. It does not carry a court, standards-body, or laboratory certification. Each lab or agency should validate it under its own procedures before relying on it in casework.

This repository is the home for the DEVI Decrypt source release. Windows builds are published at [deviops.app/tools/devi-decrypt/](https://deviops.app/tools/devi-decrypt/). `src/DeviDecrypt.Core` holds the published C# project skeleton (shared identity constants); fuller application source lands under `src/` as it is released. Community health files and brand assets follow the same layout as [DEVI Validate](https://github.com/Deviops-app/DEVI-Validate).

## What it does

- Decrypts an Apple or iCloud OpenPGP return package (`.gpg` or `.pgp`).
- Accepts a key block pasted from the provider's email, or a key file, and a passphrase when the key asks for one.
- Leaves the encrypted source alone: it is read only and is not renamed, moved, or overwritten.
- Exports a PDF verification record named by the full source SHA-256, with the source and output hashes. The record never holds the key, the passphrase, or the decrypted contents.
- Opens a return workspace for a whole Apple return and its key: every OpenPGP file is decrypted and unpacked into one folder, then browsed and searched by category.
- Lists the SHA-256 of every source and output file, with a verification record for each decrypted file.
- Runs a built-in self-test against an embedded synthetic package.

## Offline and local-first

- **Read-only on the source.** The encrypted file is opened for reading only.
- **Offline decryption.** Decryption runs on this computer and does not use the network. No telemetry is collected or sent.
- **Keys stay local.** The key and the passphrase are held in memory for the operation and are not saved. The website never receives your returns, keys, file names, or hashes.

### The one network feature: an optional update check

- It is **off by default**. It runs only when you choose **Check for updates**, or turn on "Check for updates when the app opens".
- It is one HTTPS request for a **signed** version file. It sends the product name and version and nothing else: no machine identifier, and never any case details, keys, file names, or hashes.
- A download starts only after you confirm it, and only after its SHA-256 matches the signed version file. Nothing is installed silently.

See [docs/UPDATES.md](docs/UPDATES.md) for details.

## Download

The current release is **DEVI Decrypt 1.0.3** for Windows x64. Download it from <https://deviops.app/tools/devi-decrypt/>. The installer and the portable zip are published only there. GitHub releases carry the release notes and the SHA-256 values below, not the files.

| Package | SHA-256 |
| --- | --- |
| `DEVI-Decrypt-Setup-1.0.3-win-x64.exe` (installer) | `9c83c5cedfb161bcef37240387fa847648434aa9d96d8628429af8539a71f779` |
| `DEVI-Decrypt-1.0.3-win-x64.zip` (portable) | `bd4c1d2ef8c75a397d846cd7e554d39620548e5abfea7052dfd4907deabcd39d` |

Both packages include the .NET runtime, so nothing else needs to be installed. In the portable zip, `app\DEVI-Decrypt.exe` is the desktop app.

### Check your download

Before you run a download, confirm its SHA-256 matches the table above. In PowerShell:

```powershell
Get-FileHash .\DEVI-Decrypt-Setup-1.0.3-win-x64.exe -Algorithm SHA256
```

In Command Prompt:

```bat
certutil -hashfile DEVI-Decrypt-Setup-1.0.3-win-x64.exe SHA256
```

On Linux or macOS:

```bash
sha256sum DEVI-Decrypt-Setup-1.0.3-win-x64.exe
```

The value must match this README, the GitHub release notes, and the DEVI website. If it does not match, do not run the file.

The installer, its uninstaller, and the desktop app are Authenticode-signed through Microsoft Artifact Signing, with a timestamp. A valid signature does not replace the SHA-256 check. Windows SmartScreen can still warn about a newly signed release.

## Repository layout

| Path | Contents |
| --- | --- |
| `src/` | C# solution projects (see `DeviDecrypt.sln` and `src/README.md`) |
| `docs` | Update check notes and repository status |
| `assets/brand` | DEVI brand assets used by the app and the records |
| `.github` | Issue and pull request templates, Dependabot, CI |

## Build from source

Build with the [.NET 8 SDK](https://dotnet.microsoft.com/download/dotnet/8.0) (see `global.json`):

```bash
git clone https://github.com/Deviops-app/DEVI-Decrypt.git
cd DEVI-Decrypt

dotnet restore DeviDecrypt.sln
dotnet build DeviDecrypt.sln --configuration Release
```

See [BUILDING.md](BUILDING.md) and [docs/STATUS.md](docs/STATUS.md). Community files, documentation, and brand assets mirror [DEVI Validate](https://github.com/Deviops-app/DEVI-Validate).

## Testing

See [TESTING.md](TESTING.md). Do not commit real case data, provider returns, keys, or personal information.

## Contributing

Bug reports, documentation fixes, and carefully sourced contributions are welcome. Please read [CONTRIBUTING.md](CONTRIBUTING.md) and the [Code of Conduct](CODE_OF_CONDUCT.md) first. Report security issues privately as described in [SECURITY.md](SECURITY.md). Never attach real evidence, case material, keys, or personal data to an issue or pull request.

## License

Copyright 2026 The DEVI Decrypt authors.

Licensed under the [Apache License, Version 2.0](LICENSE). See [NOTICE](NOTICE) and [THIRD-PARTY-NOTICES.md](THIRD-PARTY-NOTICES.md) for third-party components.

As Section 6 of the license states, it does not grant permission to use the DEVI name or logo, except as needed to describe where the software came from.

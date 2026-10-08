# Updates

DEVI Decrypt can check for a newer Windows build. Core product work never does this. The update check is the only network feature in the app. It is off by default and runs only when you ask for it.

## What the check does

- Start it from **Settings > Check for updates now**, or from the **More** menu (**Check for updates**).
- "Check for updates when the app opens" is in Settings and is off unless you turn it on.
- The check is one HTTPS GET of a signed version file. It sends the product name and version in the User-Agent header and nothing else: no machine identifier, no query string, and never any case details, keys, file names, or hashes.
- If the check fails or the computer is offline, the app keeps working. Core product work is not affected.

## Before anything is downloaded

1. The version file must carry a valid signature from the DEVI release key. A file with a missing or bad signature is rejected.
2. The window shows this copy's version, the published version, the release notes, and the SHA-256 of the installer and the portable zip.
3. A download starts only after you confirm it, and only from an allowed DEVI download host over HTTPS.
4. The downloaded file is checked against the SHA-256 in the signed version file. A file that does not match is thrown away.
5. Nothing is installed silently.

## Feed hosts

The app asks `downloads.deviops.app` for the signed version file. The private signing key is held by the DEVI maintainers and is not in this repository.

The feed signature protects the update channel. It is separate from the Authenticode signature on the installer and the program files. Windows SmartScreen can still warn about a newly signed release. Check the SHA-256 of any download against the value on <https://deviops.app/tools/devi-decrypt/> and in the GitHub release notes.

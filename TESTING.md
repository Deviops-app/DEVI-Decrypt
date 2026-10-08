# Testing DEVI Decrypt

Automated tests will live under `tests/` when application source is published. Until then:

- Prefer synthetic inputs only.
- Never commit provider returns, keys, passphrases, device images, case material, or personal data.
- Confirm published download SHA-256 values against [README.md](README.md) and <https://deviops.app/tools/devi-decrypt/>.

GitHub Actions runs a scaffold check on every push and pull request so community files stay present.

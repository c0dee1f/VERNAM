# Changelog

All notable changes to VERNAM are recorded here. Versions are two-part
(MAJOR.MINOR) and bump in 0.1 steps per release (1.0, 1.1, 1.2, and so on).

The `.vrn` file format has its own version byte (currently `1`) inside each file,
independent of the tool version below; old files always keep opening.

## 1.2 (2026-09-05)

Links and metadata only. No code, no crypto and no format change, so every existing .vrn file keeps opening.

- Point every PrivacyTools.io link at the bare apex, https://privacytools.io, instead of the www host. This covers the license credit link, the README, CONTRIBUTING, FORMAT.md, the page footer and the brand-kit button.
- Update the canonical URL, the og:url and the JSON-LD author URL on the standalone page to the same apex.
- Refresh the engine and UI source comments from upstream.

## 1.1 (2026-06-18)

Security hardening. No format change, every existing .vrn file keeps opening.

- Reject a file whose header asks for an out-of-range Argon2 memory or operation cost, so a malformed or hostile file cannot exhaust memory when you open it.
- Validate the key-derivation algorithm field on decrypt.
- Sanitize the recovered filename before using it as a save name (strip path separators, control and bidi-override characters, and leading dots; cap the length).
- Wipe the derived key from memory after each operation.

## 1.0.0 (2026-06-16)

- First public release.
- Drag-and-drop file encryption, fully client-side, nothing uploaded.
- Argon2id key derivation + XChaCha20-Poly1305 secretstream, via vendored libsodium.
- Auto-detects encrypt vs decrypt, streams large files to disk, standard and high-security profiles.

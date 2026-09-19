# Remote dataset refresh for offline Android references

## Enablement gate

Keep the app offline-only until all inputs are known: the immutable release location, dataset asset name, signed manifest asset name, and a pinned signing public key. A Settings action should state that refresh is not configured rather than silently failing or targeting a placeholder URL.

Add `INTERNET` only when the user has approved remote refresh and a real endpoint exists. Never put GitHub tokens, private keys, or other secrets in the APK or repository.

## Release contract

Publish a versioned release containing:

- the parsed dataset asset;
- a manifest naming that exact asset and recording byte size, SHA-256, data schema, instrument ID, dataset version date, retrieval time, parser version, and official-source URL;
- a detached Ed25519 signature over the exact manifest bytes.

Pin the Ed25519 public key in the app. HTTPS alone identifies transport, not an authorised publisher or immutable content.

## Client acceptance sequence

1. Download manifest and detached signature.
2. Verify signature using the pinned public key.
3. Reject incompatible schema, unexpected instrument ID, non-forward version, invalid size, or missing mandatory provenance.
4. Download the manifest-named dataset only after manifest acceptance.
5. Check size, SHA-256, JSON parse/schema, and embedded metadata consistency.
6. Write to a temporary file, fsync/close, then atomically replace the active downloaded dataset.
7. Retain the bundled or last verified dataset on every failure; surface a concise, non-sensitive failure state and the last successful refresh time in Settings.

## UI labels

- “Last local check” describes successful bundled-data parsing/integrity validation during launch.
- “Last successful refresh” describes a completed remote update only.
- Avoid “sync” when no remote source exists; it implies a network exchange.

# Tab5 ROM Store

This repository contains release artifacts only. It intentionally contains no
firmware source, plaintext ROM image, ELF/map file, or private key.

The launcher accepts catalog schema 1 for `m5stack-tab5-p4` and layout
`tab5-16m-v1`. Each ROM is encrypted in the RSA format used by
`espressif/esp_encrypted_img` 2.3.0 (RSA-3072 PKCS#1 v1.5 key wrapping plus
AES-256-GCM). `catalog/v1/catalog.json.sig` is a binary DER ECDSA P-256/SHA-256
signature over the exact bytes of `catalog/v1/catalog.json`. Public-key SPKI
SHA-256 fingerprints are recorded in `keys/fingerprints.json`.

A client must verify the catalog signature before trusting any URL or digest,
then verify the encrypted download size and SHA-256, authenticate/decrypt the
image, and finally verify the plaintext image size and SHA-256 before selecting
the OTA partition.

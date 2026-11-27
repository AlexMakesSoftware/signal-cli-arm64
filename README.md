# signal-cli-arm64

[signal-cli](https://github.com/AsamK/signal-cli) for Linux on 64-bit ARM (aarch64), such as a Raspberry Pi.

signal-cli's own releases only include Signal's native library (`libsignal_jni`) for x86_64 Linux. This repo
builds that library for aarch64 from [Signal's source](https://github.com/signalapp/libsignal) on GitHub's ARM
runners, swaps it into signal-cli, and publishes the result as a release with a GitHub artifact attestation.

A workflow checks for a new signal-cli release once a day and builds it. Each release contains:

- `signal-cli-<version>-linux-aarch64.tar.gz`: signal-cli, unchanged except for the library swap. Its
  signature is checked against AsamK's release key before anything is built.
- `signal-cli-<version>-linux-aarch64.json`: the signal-cli, libsignal and Java versions, the newest glibc the
  library needs, and the library's SHA-256.
- `SHA256SUMS`.

## Using a release

Needs Java at the version given in the release notes (25 for signal-cli 0.14).

```
gh attestation verify signal-cli-<version>-linux-aarch64.tar.gz --repo AlexMakesSoftware/signal-cli-arm64
tar -xzf signal-cli-<version>-linux-aarch64.tar.gz
signal-cli-<version>/bin/signal-cli --version
```

The attestation proves the package was built by this repo's workflow, from the commit it names.

## Licence

GPL-3.0, the same as signal-cli. Each release is built from the signal-cli and libsignal tags it names.

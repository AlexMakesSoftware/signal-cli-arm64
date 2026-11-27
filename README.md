# signal-cli-arm64

[signal-cli](https://github.com/AsamK/signal-cli) for Linux on 64-bit ARM (aarch64), such as a Raspberry Pi.

signal-cli's own releases only include Signal's native library (`libsignal_jni`) for x86_64 Linux. This repo
builds that library for aarch64 from [Signal's source](https://github.com/signalapp/libsignal) on GitHub's ARM
runners, swaps it into signal-cli, and publishes the result as a release with a GitHub artifact attestation.

Work in progress: nothing is published yet.

## Licence

GPL-3.0, the same as signal-cli. Each release is built from the signal-cli and libsignal tags it names.

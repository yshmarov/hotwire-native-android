# Navigation lifecycle fix for Hotwire Native Android 1.4.1

This branch starts from upstream 1.4.1 (`56e02c8d9488370ddfdaf325f777ecf89a2e5b8d`) and carries the patch and regressions from [upstream PR #226](https://github.com/hotwired/hotwire-native-android/pull/226).

JitPack runs both modules' release tests and lint before publishing. The modules share a Maven group because navigation calls core APIs restricted to the library group. Consumers pin both artifacts to the same commit. Core's implementation matches upstream 1.4.1.

Use a fresh branch from a reviewed upstream release tag for the next upgrade. Carry forward the lifecycle fix only until it ships in an official release. Re-run the fork tests, verify the artifact metadata and test the consuming app before updating its pin.

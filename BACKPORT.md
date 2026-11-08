# Navigation lifecycle backport for 1.3.1

This branch is based on upstream tag 1.3.1 (`a49cb9bf87e095d52c2f9529f951c78f20b2dc23`). It backports the navigation continuation fix from [upstream PR #226](https://github.com/hotwired/hotwire-native-android/pull/226), without adopting subsequent library changes.

Only `Navigator.navigateWhenReady` changes in production source. Nine regression cases cover obsolete hosts and views, activity destruction, detachment cleanup and valid navigation. The 1.3.1-specific bridge assertion verifies that dropping stale navigation still releases bridge ownership.

`jitpack.yml` runs the navigation module's release tests and lint before publishing that module. Its dependency is the official `dev.hotwire:core:1.3.1` artifact; no forked core is bundled. JitPack supplies `GROUP`, `ARTIFACT` and `VERSION` for the publication coordinates. Consumers should pin the full tested commit SHA, rather than a moving branch.

Run locally with Java 17 and the Android SDK configured:

```sh
./gradlew :navigation-fragments:testReleaseUnitTest :navigation-fragments:lint
```

Return to the official navigation artifact once an upstream release includes the fix and has passed the consuming application's regressions.

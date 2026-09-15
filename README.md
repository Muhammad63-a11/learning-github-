# AI App Doctor — Expo GitHub Actions APK Builder

This version is designed for Expo / React Native projects rather than starting from a Gradle project.

## Core workflow

Expo ZIP
→ project detection
→ Node/package-manager detection
→ dependency installation
→ Expo configuration inspection
→ `expo prebuild` (when native Android output is absent)
→ Expo-generated Android project
→ Gradle APK build
→ failure diagnosis
→ bounded safe repair
→ rebuild
→ APK integrity/signature validation
→ final APK + diagnostic report

## Diagnostics

Every known failure is intended to be explained at two levels:

1. **Human explanation** — what happened, why it matters, and what the Doctor is doing.
2. **Technical diagnosis** — category, stage, confidence, evidence, and the original error tail.

Known diagnostic families include:

- Node / Expo SDK incompatibility
- JavaScript dependency conflicts
- Expo config/config-plugin failures
- Android SDK problems
- JDK/Java compatibility
- Gradle memory failures
- Android resource/manifest failures
- Kotlin/native module failures
- network/package registry failures
- invalid/corrupt APK artifacts

The original logs remain available for developers.

## Important safety behavior

The Doctor must not blindly rewrite application source code merely because a build failed. If a problem cannot be repaired with high confidence, it should report the cause and preserve the evidence rather than making a destructive guess.

## Output

The workflow uploads the validated APK and diagnostic artifacts so a non-technical user can understand the result while a developer can inspect the underlying evidence.

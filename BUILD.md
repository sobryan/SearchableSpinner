# Build Process Documentation

This document describes the build process for the SearchableSpinner library.

## Prerequisites

### Required Software

- **JDK 17 or higher**
  - Download from: https://adoptium.net/
  - Verify: `java -version`
  
- **Android SDK**
  - Install via Android Studio or command-line tools
  - Required API level: 34
  - Set `ANDROID_HOME` environment variable

- **Gradle 8.5** (included via wrapper)
  - No separate installation needed
  - Wrapper scripts: `gradlew` (Linux/Mac) or `gradlew.bat` (Windows)

### Optional Tools

- Android Studio (for development and debugging)
- Git (for version control)

## Project Structure

```
SearchableSpinner/
├── .github/workflows/     # GitHub Actions CI/CD
│   ├── build.yml         # Build and test workflow
│   ├── publish.yml       # Maven Central publishing
│   └── security.yml      # Security scanning
├── sample/               # Sample Android app
│   ├── src/
│   └── build.gradle
├── searchablespinnerlibrary/  # Main library
│   ├── src/
│   └── build.gradle
├── build.gradle          # Root build configuration
├── settings.gradle       # Project settings
├── gradle.properties     # Gradle properties
└── gradle/wrapper/       # Gradle wrapper files
```

## Build Commands

### Clean Build

Remove all build artifacts:
```bash
./gradlew clean
```

### Build Library

Build the library module:
```bash
./gradlew :searchablespinnerlibrary:build
```

This will:
1. Compile Java sources
2. Process resources
3. Generate AAR (Android Archive)
4. Run lint checks
5. Run unit tests

Output: `searchablespinnerlibrary/build/outputs/aar/`

### Build Sample App

Build the sample application:
```bash
./gradlew :sample:build
```

Output: `sample/build/outputs/apk/`

### Build Everything

Build all modules:
```bash
./gradlew build
```

### Run Tests

Run all tests:
```bash
./gradlew test
```

Run library tests only:
```bash
./gradlew :searchablespinnerlibrary:test
```

### Check Dependencies

List all dependencies:
```bash
./gradlew dependencies
```

Check for dependency updates:
```bash
./gradlew dependencyUpdates
```

### Lint

Run Android Lint:
```bash
./gradlew lint
```

View lint report:
```
searchablespinnerlibrary/build/reports/lint-results.html
```

## Publishing

### Generate JARs

Generate sources JAR:
```bash
./gradlew androidSourcesJar
```

Generate Javadoc JAR:
```bash
./gradlew androidJavadocsJar
```

### Publish to Local Maven

Install to local Maven repository (~/.m2/repository):
```bash
./gradlew publishToMavenLocal
```

### Publish to Maven Central

See [PUBLISHING.md](PUBLISHING.md) for complete instructions.

Quick publish:
```bash
./gradlew :searchablespinnerlibrary:publishReleasePublicationToSonatypeRepository
```

## Continuous Integration

### GitHub Actions

The project uses GitHub Actions for CI/CD:

1. **Build Workflow** (`.github/workflows/build.yml`)
   - Triggers: Push to main branches, Pull requests
   - Actions: Build, test, upload artifacts
   
2. **Publish Workflow** (`.github/workflows/publish.yml`)
   - Triggers: GitHub releases, manual trigger
   - Actions: Build, sign, publish to Maven Central
   
3. **Security Workflow** (`.github/workflows/security.yml`)
   - Triggers: Push, PR, weekly schedule
   - Actions: Dependency scan, CodeQL analysis, wrapper validation

### Local CI Simulation

Run the same checks as CI:
```bash
# Build check
./gradlew build --no-daemon

# Security check
./gradlew dependencies

# Lint check
./gradlew lint
```

## Build Variants

The library supports two build types:

### Debug
```bash
./gradlew :searchablespinnerlibrary:assembleDebug
```
Output: `searchablespinnerlibrary/build/outputs/aar/searchablespinnerlibrary-debug.aar`

### Release
```bash
./gradlew :searchablespinnerlibrary:assembleRelease
```
Output: `searchablespinnerlibrary/build/outputs/aar/searchablespinnerlibrary-release.aar`

## Troubleshooting

### Issue: "SDK location not found"
**Solution:** Create `local.properties` with:
```properties
sdk.dir=/path/to/android/sdk
```

### Issue: "Java version mismatch"
**Solution:** Set JAVA_HOME to JDK 17:
```bash
export JAVA_HOME=/path/to/jdk-17
```

### Issue: "Gradle daemon issues"
**Solution:** Stop all daemons:
```bash
./gradlew --stop
```

### Issue: "Dependency download failures"
**Solution:** 
1. Check internet connection
2. Clear Gradle cache: `rm -rf ~/.gradle/caches/`
3. Retry with: `./gradlew build --refresh-dependencies`

### Issue: "Build fails with memory error"
**Solution:** Increase memory in `gradle.properties`:
```properties
org.gradle.jvmargs=-Xmx4096m -Dfile.encoding=UTF-8
```

## Performance Tips

### Enable Parallel Builds
In `gradle.properties`:
```properties
org.gradle.parallel=true
```

### Enable Build Cache
```properties
org.gradle.caching=true
```

### Use Gradle Daemon
```properties
org.gradle.daemon=true
```

## Build Outputs

### Library (AAR)
- Location: `searchablespinnerlibrary/build/outputs/aar/`
- Contains: Compiled classes, resources, AndroidManifest.xml

### Sample App (APK)
- Debug: `sample/build/outputs/apk/debug/sample-debug.apk`
- Release: `sample/build/outputs/apk/release/sample-release.apk`

### Documentation
- Javadoc: `searchablespinnerlibrary/build/docs/javadoc/`
- Lint Reports: `searchablespinnerlibrary/build/reports/`

### Test Results
- Unit Tests: `searchablespinnerlibrary/build/reports/tests/`
- Coverage: `searchablespinnerlibrary/build/reports/coverage/`

## Environment Variables

### Required
- `ANDROID_HOME` or `ANDROID_SDK_ROOT`: Path to Android SDK

### Optional (for publishing)
- `OSSRH_USERNAME`: Sonatype username
- `OSSRH_PASSWORD`: Sonatype password
- `SIGNING_KEY`: GPG signing key (base64)
- `SIGNING_PASSWORD`: GPG key passphrase

## Gradle Properties

Key properties in `gradle.properties`:

```properties
# Project settings
android.useAndroidX=true
android.nonTransitiveRClass=true

# Performance
org.gradle.jvmargs=-Xmx2048m -Dfile.encoding=UTF-8
org.gradle.parallel=true

# Publishing (set in local.properties or CI secrets)
# ossrhUsername=your_username
# ossrhPassword=your_password
# signingKey=your_gpg_key
# signingPassword=your_gpg_password
```

## Additional Resources

- [Gradle Build Tool](https://gradle.org/)
- [Android Gradle Plugin](https://developer.android.com/studio/releases/gradle-plugin)
- [Maven Publishing](https://docs.gradle.org/current/userguide/publishing_maven.html)
- [GitHub Actions](https://docs.github.com/en/actions)

## Support

For build-related issues:
1. Check this documentation
2. Review GitHub Actions logs
3. Open an issue with build logs
4. Include Gradle version and environment details

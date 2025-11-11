# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.3.2] - 2025-11-11

### 🎉 Major Update - Build System Modernization

This release represents a complete modernization of the build system and dependencies, transitioning from deprecated tools to current, maintained alternatives.

### Added

- ✅ **Maven Central Publishing Support**
  - Replaced deprecated Bintray with Maven Central
  - Configured `maven-publish` plugin
  - Added GPG signing for artifact verification
  - See [PUBLISHING.md](PUBLISHING.md) for details

- 🔒 **Security & Quality Assurance**
  - GitHub Actions workflow for automated builds (`.github/workflows/build.yml`)
  - GitHub Actions workflow for Maven Central publishing (`.github/workflows/publish.yml`)
  - Automated security scanning workflow (`.github/workflows/security.yml`)
  - CodeQL security analysis
  - Weekly dependency vulnerability checks
  - Gradle wrapper validation

- 📚 **Comprehensive Documentation**
  - [PUBLISHING.md](PUBLISHING.md) - Maven Central publishing guide
  - [SECURITY.md](SECURITY.md) - Security policy and vulnerability status
  - [MIGRATION_GUIDE.md](MIGRATION_GUIDE.md) - Upgrade instructions from 1.3.1
  - [BUILD.md](BUILD.md) - Detailed build process documentation
  - [CHANGELOG.md](CHANGELOG.md) - This file

- ✨ **Build Improvements**
  - AndroidX namespace support
  - Java 8 source/target compatibility
  - Modern Gradle properties (parallel builds, caching)
  - Non-transitive R classes for better build performance

### Changed

- ⬆️ **Gradle**: 2.10 → 8.5
- ⬆️ **Android Gradle Plugin**: 2.1.0 → 7.4.2
- ⬆️ **compileSdk**: 23 → 34
- ⬆️ **targetSdk**: 23 → 34
- 🔄 **Dependencies**: Android Support Libraries → AndroidX
  - `androidx.appcompat:appcompat:1.6.1`
  - `androidx.fragment:fragment:1.6.2`
- 🔄 **Repositories**: JCenter (deprecated) → Maven Central + Google Maven
- 🔄 **Dependency Declarations**: `compile` → `implementation`
- 🔄 **Fragment API**: `android.app.DialogFragment` → `androidx.fragment.app.DialogFragment`
- 🔄 **Activity Requirement**: Now requires `FragmentActivity` or `AppCompatActivity`

### Removed

- ❌ Bintray publishing configuration (service shut down)
- ❌ JCenter repository references (service shut down)
- ❌ Deprecated `compile` dependency syntax
- ❌ Old Android Support Library dependencies

### Fixed

- 🐛 Compatibility with modern Android development environments
- 🐛 Updated for Java 17 runtime compatibility
- 🐛 Fixed deprecated API usage throughout the codebase

### Security

- ✅ **Zero Vulnerabilities**: All dependencies verified against GitHub Advisory Database
  - `androidx.appcompat:appcompat:1.6.1` - No known vulnerabilities
  - `androidx.fragment:fragment:1.6.2` - No known vulnerabilities
- 🔒 Automated security scanning via GitHub Actions
- 🔍 CodeQL analysis for code security issues
- 📊 Weekly dependency vulnerability checks

### Migration Notes

**Breaking Changes:**
1. Must migrate to AndroidX (if not already done)
2. Activities must extend `FragmentActivity` or `AppCompatActivity`
3. Update repository from JCenter to Maven Central

**See [MIGRATION_GUIDE.md](MIGRATION_GUIDE.md) for detailed upgrade instructions.**

---

## [1.3.1] - Previous Release

### Changed
- Bug fixes

## [1.3.0] - Previous Release

### Added
- Hint text feature
- Text changed listener

### Changed
- Removed transparent black view appearing while typing

## [1.2.0] - Previous Release

### Fixed
- Crash on orientation change when dialog is visible (Issue #7)
- Data refresh when setting adapter again (Issue #6)

## [1.1.0] - Previous Release

### Added
- Title text customization
- Positive button text customization
- Positive button click listener

## [1.0.2] - Previous Release

### Fixed
- Multidex issue

## [1.0.0] - Initial Release

### Added
- Initial release of SearchableSpinner
- Dialog-based spinner with search functionality
- Basic customization options

---

## Version Comparison

| Version | Gradle | AGP   | Android API | Support Lib | Status       |
|---------|--------|-------|-------------|-------------|--------------|
| 1.3.2   | 8.5    | 7.4.2 | 34          | AndroidX    | ✅ Current   |
| 1.3.1   | 2.10   | 2.1.0 | 23          | Support     | ⚠️ Outdated |
| < 1.3.1 | 2.10   | 2.1.0 | ≤23         | Support     | ❌ Deprecated|

---

## Support and Contributing

- **Report Issues**: [GitHub Issues](https://github.com/sobryan/SearchableSpinner/issues)
- **Security Issues**: See [SECURITY.md](SECURITY.md)
- **Contributing**: Pull requests welcome!
- **Build Instructions**: See [BUILD.md](BUILD.md)
- **Publishing**: See [PUBLISHING.md](PUBLISHING.md)

## License

Apache License 2.0 - See [LICENSE](LICENSE) for details.

Copyright 2015-2016 Mitesh Pithadiya  
Copyright 2025 SearchableSpinner Contributors

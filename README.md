# SearchableSpinner 
[![Android Arsenal](https://img.shields.io/badge/Android%20Arsenal-SearchableSpinner-green.svg?style=true)](https://android-arsenal.com/details/1/3272)
[![Build Status](https://github.com/sobryan/SearchableSpinner/workflows/Build%20and%20Test/badge.svg)](https://github.com/sobryan/SearchableSpinner/actions)
[![Security](https://github.com/sobryan/SearchableSpinner/workflows/Security%20Scanning/badge.svg)](https://github.com/sobryan/SearchableSpinner/security)

Spinner with searchable items.

Searchable Spinner is a dialog spinner with the search feature which allows to search the items loaded in the spinner.

![Alt text](https://github.com/miteshpithadiya/SearchableSpinner/blob/master/searchablespinnerlibrary/src/main/res/nobleltevzwLMY47XMeditab02192016201518.gif "Searchable Spinner")

## Features

- 🔍 Search functionality in spinner
- 📱 AndroidX support
- 🎨 Customizable title and positive button
- 🔄 Text change listener support
- ✅ No known security vulnerabilities
- 🔒 Regular security scanning

## Installation

### Gradle (when published to Maven Central)

```gradle
dependencies {
    implementation 'com.toptoche.searchablespinner:searchablespinnerlibrary:1.3.2'
}
```

**Note**: This library is being migrated from JCenter/Bintray to Maven Central. Publishing setup is complete - see [PUBLISHING.md](PUBLISHING.md) for details.

# Usage
    <com.toptoche.searchablespinnerlibrary.SearchableSpinner
            android:layout_width="wrap_content"
            android:layout_height="wrap_content" />

    searchableSpinner.setTitle("Select Item");
    searchableSpinner.setPositiveButton("OK");
    
# Changelog

## [1.3.2] - 2025-11-11

### 🎉 Major Update - Modernized Build System

#### Changed
- ⬆️ **Upgraded Gradle** from 2.10 to 8.5
- ⬆️ **Upgraded Android Gradle Plugin** from 2.1.0 to 7.4.2
- ⬆️ **Updated compileSdk and targetSdk** from API 23 to API 34
- 🔄 **Migrated to AndroidX** from deprecated Android Support Libraries
- 📦 **Replaced JCenter with Maven Central** (JCenter shutdown)
- 🔄 **Replaced deprecated `compile` with `implementation`**

#### Added
- ✅ **Maven Central Publishing** support (replacing deprecated Bintray)
- 🔒 **GitHub Actions CI/CD** workflows (build, test, publish, security scanning)
- 📝 **PUBLISHING.md** - Comprehensive Maven Central publishing guide
- 🛡️ **SECURITY.md** - Security policy and vulnerability status
- 🔍 **Automated Security Scanning** - Weekly dependency vulnerability checks
- ✅ **CodeQL Analysis** - Automated code security scanning
- ✅ **No Known Vulnerabilities** - All dependencies verified

#### Removed
- ❌ Deprecated Bintray publishing configuration
- ❌ Deprecated JCenter repository references

#### Dependencies
- `androidx.appcompat:appcompat:1.6.1` (migrated from support-v7)
- `androidx.fragment:fragment:1.6.2` (migrated from support-v4)

### Previous Versions

 * <b>1.3.1</b>
    * Bug fixes.
 * <b>1.3.0</b>
    * Added hint feature.
    * Removed the transparent black view appearing while typing.
    * Added a new feature for text changed listener.
 * <b>1.2.0</b>
    * Prevented crashing when changing the orientation when the dialog is visible on screen (Issue #7).
    * Data now getting refreshed on setting the adapter again (Issue #6).
 * <b>1.1.0</b>
    * New Feature to set the text of the title.
    * New Feature to set the text of the positive button as well as set a click listener on that button.
 * <b>1.0.2</b>
    * Resolved the multidex issue.
 * <b>1.0.0</b>
    * Initial Release

## Building from Source

### Prerequisites

- JDK 17 or higher
- Android SDK with API 34
- Gradle 8.5 (wrapper included)

### Build Commands

```bash
# Build the library
./gradlew :searchablespinnerlibrary:build

# Build the sample app
./gradlew :sample:build

# Run tests
./gradlew test

# Check for security vulnerabilities
./gradlew dependencies
```

## Publishing

See [PUBLISHING.md](PUBLISHING.md) for detailed instructions on publishing to Maven Central.

## Security

This project follows security best practices:
- ✅ No known vulnerabilities in dependencies
- 🔒 Automated security scanning via GitHub Actions
- 📊 Weekly dependency vulnerability checks
- 🔍 CodeQL security analysis

See [SECURITY.md](SECURITY.md) for our security policy and how to report vulnerabilities.

## Contributing

Contributions are welcome! Please:
1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Run tests and security scans
5. Submit a pull request

## Documentation

- [PUBLISHING.md](PUBLISHING.md) - Publishing to Maven Central
- [SECURITY.md](SECURITY.md) - Security policy and status

## License

    Copyright 2015-2016 Mitesh Pithadiya
    Copyright 2025 SearchableSpinner Contributors

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

     http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.

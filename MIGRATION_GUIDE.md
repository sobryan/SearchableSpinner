# Migration Guide - Version 1.3.2

This document outlines the changes made in version 1.3.2 and what users need to know when upgrading.

## Breaking Changes

### AndroidX Migration

The library has been migrated from Android Support Libraries to AndroidX.

**Before (1.3.1 and earlier):**
```xml
<com.toptoche.searchablespinnerlibrary.SearchableSpinner
    android:layout_width="wrap_content"
    android:layout_height="wrap_content" />
```

**After (1.3.2):**
```xml
<!-- Usage remains the same -->
<com.toptoche.searchablespinnerlibrary.SearchableSpinner
    android:layout_width="wrap_content"
    android:layout_height="wrap_content" />
```

However, your app **must** use AndroidX. If you haven't migrated yet:

1. In Android Studio: `Refactor > Migrate to AndroidX`
2. Or add to `gradle.properties`:
   ```properties
   android.useAndroidX=true
   android.enableJetifier=true
   ```

### FragmentActivity Requirement

Activities using SearchableSpinner must extend `FragmentActivity` or `AppCompatActivity` (which extends FragmentActivity).

**Before:**
```java
public class MainActivity extends Activity {
    // ...
}
```

**After:**
```java
public class MainActivity extends AppCompatActivity {
    // ...
}
```

## Dependency Changes

### Gradle Version

**Before:** Gradle 2.10
**After:** Gradle 8.5

Your project's Gradle wrapper should be compatible. Update if needed:
```bash
./gradlew wrapper --gradle-version=8.5
```

### Repository Changes

**Before:**
```gradle
repositories {
    jcenter() // Deprecated and shut down
}
```

**After:**
```gradle
repositories {
    google()
    mavenCentral()
}
```

### Dependency Declaration

**Before:**
```gradle
dependencies {
    compile 'com.toptoche.searchablespinner:searchablespinnerlibrary:1.3.1'
}
```

**After:**
```gradle
dependencies {
    implementation 'com.toptoche.searchablespinner:searchablespinnerlibrary:1.3.2'
}
```

## Build Configuration Updates

### compileSdkVersion and targetSdkVersion

**Before:**
```gradle
android {
    compileSdkVersion 23
    targetSdkVersion 23
}
```

**After:**
```gradle
android {
    compileSdk 34
    targetSdk 34
}
```

### Build Tools

Your project should use compatible build tools:
```gradle
android {
    compileSdk 34
    
    defaultConfig {
        minSdk 15  // Unchanged - still supports Android 4.0.3+
        targetSdk 34
    }
}
```

## Publishing Changes

The library is being migrated from Bintray/JCenter (shutdown) to Maven Central.

**Old (deprecated):**
```gradle
// Published on Bintray
dependencies {
    implementation 'com.toptoche.searchablespinner:searchablespinnerlibrary:1.3.1'
}
```

**New (Maven Central):**
```gradle
// Will be published on Maven Central
dependencies {
    implementation 'com.toptoche.searchablespinner:searchablespinnerlibrary:1.3.2'
}
```

**Note:** Until the library is published to Maven Central, you can:
1. Use JitPack: [![](https://jitpack.io/v/sobryan/SearchableSpinner.svg)](https://jitpack.io/#sobryan/SearchableSpinner)
2. Build from source and use as a local dependency

## What Stays the Same

✅ **API remains unchanged** - All public methods work exactly as before
✅ **minSdkVersion** - Still supports Android 4.0.3+ (API 15)
✅ **License** - Apache 2.0
✅ **Usage patterns** - No code changes required in your implementation

## New Features

✅ **Better security** - Regular vulnerability scanning
✅ **Modern tooling** - Latest Gradle and Android Gradle Plugin
✅ **CI/CD** - Automated builds and testing via GitHub Actions
✅ **Better maintenance** - Easier to contribute and maintain

## Testing Your Migration

1. Update the dependency in your `build.gradle`
2. Ensure your app uses AndroidX
3. Build your project: `./gradlew build`
4. Run your tests
5. Test the SearchableSpinner functionality in your app

## Troubleshooting

### Issue: "AndroidX not found"
**Solution:** Add to `gradle.properties`:
```properties
android.useAndroidX=true
android.enableJetifier=true
```

### Issue: "Fragment not found"
**Solution:** Ensure your Activity extends `AppCompatActivity`:
```java
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {
    // ...
}
```

### Issue: "Dependency not found"
**Solution:** Ensure you have the correct repositories:
```gradle
repositories {
    google()
    mavenCentral()
}
```

## Rollback

If you need to rollback to 1.3.1:
```gradle
dependencies {
    implementation 'com.toptoche.searchablespinner:searchablespinnerlibrary:1.3.1'
}
```

Note: Version 1.3.1 uses deprecated dependencies and JCenter, which is no longer maintained.

## Support

- GitHub Issues: [Report issues](https://github.com/sobryan/SearchableSpinner/issues)
- Security: See [SECURITY.md](SECURITY.md)
- Publishing: See [PUBLISHING.md](PUBLISHING.md)

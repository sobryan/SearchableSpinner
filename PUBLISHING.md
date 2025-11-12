# Publishing to Maven Central

This document describes how to publish the SearchableSpinner library to Maven Central.

## Prerequisites

1. **Sonatype Account**: Create an account at https://s01.oss.sonatype.org/
2. **Group ID Verification**: Verify ownership of the `com.toptoche.searchablespinner` group ID
3. **GPG Key**: Generate a GPG key pair for signing artifacts

### Setting up GPG Keys

```bash
# Generate a new GPG key
gpg --gen-key

# List your keys
gpg --list-keys

# Export your private key (replace KEY_ID with your actual key ID)
gpg --export-secret-keys KEY_ID | base64

# Upload your public key to a key server
gpg --keyserver keyserver.ubuntu.com --send-keys KEY_ID
```

## Configuration

### Local Development

Create a `local.properties` file in the root directory (this file is git-ignored):

```properties
ossrhUsername=your_sonatype_username
ossrhPassword=your_sonatype_password
signingKey=your_gpg_private_key_base64
signingPassword=your_gpg_passphrase
```

### GitHub Secrets (for CI/CD)

Add the following secrets to your GitHub repository:

- `OSSRH_USERNAME`: Your Sonatype username
- `OSSRH_PASSWORD`: Your Sonatype password
- `SIGNING_KEY`: Your GPG private key (base64 encoded)
- `SIGNING_PASSWORD`: Your GPG key passphrase

## Publishing Process

### Manual Publishing

1. Update the version in `searchablespinnerlibrary/build.gradle`:
   ```gradle
   libraryVersion = '1.3.2'
   ```

2. Build and publish:
   ```bash
   ./gradlew :searchablespinnerlibrary:build
   ./gradlew :searchablespinnerlibrary:publishReleasePublicationToSonatypeRepository
   ```

3. Login to https://s01.oss.sonatype.org/
4. Navigate to "Staging Repositories"
5. Find your staging repository
6. Click "Close" to validate the artifacts
7. Once validation passes, click "Release" to publish to Maven Central

### Automated Publishing via GitHub Actions

Publishing is automated through GitHub Actions:

1. Create a new release on GitHub
2. The publish workflow will automatically trigger
3. Artifacts will be uploaded to Sonatype staging repository
4. Manually close and release the staging repository on Sonatype

## Version Management

- Use semantic versioning: MAJOR.MINOR.PATCH
- Update version in `searchablespinnerlibrary/build.gradle`
- Update version in README.md
- Create a git tag for each release

## Troubleshooting

### Signing Errors

If you encounter signing errors, ensure:
- Your GPG key is properly formatted (base64 encoded)
- The passphrase is correct
- The key hasn't expired

### Upload Errors

If upload fails:
- Verify your Sonatype credentials
- Check that the group ID is verified in your Sonatype account
- Ensure all required POM metadata is present

### Validation Errors

Common validation errors:
- Missing sources or javadoc JARs
- Invalid POM metadata
- Unsigned artifacts
- Invalid group ID

## References

- [Sonatype OSSRH Guide](https://central.sonatype.org/publish/publish-guide/)
- [Maven Central Publishing Requirements](https://central.sonatype.org/publish/requirements/)
- [Gradle Maven Publish Plugin](https://docs.gradle.org/current/userguide/publishing_maven.html)

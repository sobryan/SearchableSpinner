# Security Policy

## Supported Versions

| Version | Supported          |
| ------- | ------------------ |
| 1.3.2   | :white_check_mark: |
| < 1.3.2 | :x:                |

## Dependency Management

This project uses the following main dependencies:

- **AndroidX AppCompat**: 1.6.1
- **AndroidX Fragment**: 1.6.2
- **Android Gradle Plugin**: 7.4.2
- **Gradle**: 8.5

All dependencies are regularly checked for security vulnerabilities using:
- GitHub Dependabot
- OWASP Dependency-Check
- CodeQL Security Scanning

## Security Scanning

### Automated Scanning

Security scans are automatically run:
- On every push to main branches
- On every pull request
- Weekly on Monday at 00:00 UTC
- Manually via workflow dispatch

### Manual Scanning

To manually check for security vulnerabilities:

```bash
# Check all dependencies
./gradlew dependencies

# Run security scan (if OWASP plugin is added)
./gradlew dependencyCheckAnalyze
```

## Vulnerability Status

**Current Status**: ✅ No Known Vulnerabilities

Last Checked: 2025-11-11

### Dependency Audit Results

All current dependencies have been scanned against the GitHub Advisory Database:
- ✅ androidx.appcompat:appcompat:1.6.1 - No vulnerabilities
- ✅ androidx.fragment:fragment:1.6.2 - No vulnerabilities

## Reporting a Vulnerability

If you discover a security vulnerability, please follow these steps:

1. **Do NOT** open a public issue
2. Email the maintainers directly at [security contact email]
3. Provide detailed information:
   - Description of the vulnerability
   - Steps to reproduce
   - Potential impact
   - Suggested fix (if available)

### Response Timeline

- **Initial Response**: Within 48 hours
- **Status Update**: Within 7 days
- **Fix Release**: Depends on severity
  - Critical: Within 7 days
  - High: Within 30 days
  - Medium: Within 60 days
  - Low: Best effort

## Security Best Practices

### For Users of this Library

1. Always use the latest version
2. Monitor for security updates
3. Enable GitHub security alerts for your repository
4. Review the changelog for security-related updates

### For Contributors

1. Keep dependencies up to date
2. Run security scans before submitting PRs
3. Follow secure coding practices
4. Never commit sensitive information (API keys, passwords, etc.)
5. Use signed commits when possible

## Security Improvements in Version 1.3.2

- ✅ Upgraded from deprecated Support Libraries to AndroidX
- ✅ Removed deprecated Bintray dependencies
- ✅ Updated to modern Android Gradle Plugin (7.4.2)
- ✅ Updated to Gradle 8.5
- ✅ Added automated security scanning workflows
- ✅ All dependencies verified against GitHub Advisory Database
- ✅ Minimum SDK updated with latest security patches

## License Compliance

This project is licensed under Apache License 2.0. All dependencies are compatible with this license:

- AndroidX libraries: Apache License 2.0
- Gradle: Apache License 2.0

## Additional Resources

- [Android Security Best Practices](https://developer.android.com/topic/security/best-practices)
- [OWASP Mobile Security](https://owasp.org/www-project-mobile-security/)
- [GitHub Security Advisories](https://github.com/advisories)
- [Sonatype OSS Index](https://ossindex.sonatype.org/)

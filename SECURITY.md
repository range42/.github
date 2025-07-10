# Security Policy

## Range42 Security Advisories

You can find all Range42 security advisories on the [Range42 project website](https://www.range42.net/security#advisories).

## Supported Versions

:todo: Once we have proper versioning we will update

Range42 maintains security support for the following versions:

| Version | Supported          | EOL Date |
| ------- | ------------------ | -------- |
| x.y     | :white_check_mark: | TBD      |
| x.y.z   | :white_check_mark: | 2025-12-31 |
| x.y.z   | :warning: Limited  | 2024-12-31 |
| < x.y   | :x:                | Ended    |

**Note**: Limited support means only critical security vulnerabilities will be addressed.

## Reporting Security Vulnerabilities

Reporting security vulnerabilities is of critical importance to us, as Range42 is deployed in multiple environments including production cybersecurity training systems, educational institutions, and corporate security programs.

### How to Report

**For security vulnerabilities, please DO NOT use public GitHub issues.**

Instead, please send your report directly to:
- **Primary**: [security@range42.net](mailto:security@range42.net)
- **CC**: [info@circl.lu](mailto:info@circl.lu)

### Encryption (Recommended)

For sensitive reports, please encrypt your message using our PGP keys:

:todo: Generate PGP Keys for the project.

```
Primary Key: CA57 2205 C002 4E06 BA70 BE89 EAAD CFFC 22BD 4CD5
Secondary Key: 3F4D 8CF6 08F9 4F88 2815 2CB1 69A2 0F50 9BE4 AEE9
```

:todo: Once webiste is up and running use: Security.txt (RFC 9116) /.well-known/security.txt

You can find our public keys at [https://www.range42.net/security/pgp-keys](https://www.range42.net/security/pgp-keys).

### What to Include in Your Report

Please include as much of the following information as possible:

- **Vulnerability Type**: (e.g., RCE, XSS, SQL injection, privilege escalation)
- **Affected Component**: Specific Range42 component or module
- **Affected Versions**: Range42 versions that contain the vulnerability
- **Attack Vector**: How the vulnerability can be exploited
- **Impact Assessment**: Potential consequences of exploitation
- **Proof of Concept**: Steps to reproduce (if safe to include)
- **Suggested Fix**: If you have recommendations for remediation
- **Disclosure Timeline**: Your preferred timeline for public disclosure
- **Attribution**: How you would like to be credited (if at all)

### Response Timeline

We are committed to addressing security vulnerabilities promptly:

- **Initial Response**: Within 24 hours of report receipt
- **Vulnerability Assessment**: Within 48 hours
- **Fix Development**: Critical vulnerabilities within 48-72 hours
- **Patch Release**: Within 5-7 days for critical issues
- **Public Disclosure**: Coordinated with reporter, typically 30-90 days after fix

### Severity Classification

We use the following severity levels based on CVSS 3.1:

| Severity | CVSS Score | Response Time | Example |
|----------|------------|---------------|---------|
| Critical | 9.0 - 10.0 | 24-48 hours | Remote code execution, authentication bypass |
| High     | 7.0 - 8.9  | 48-72 hours | Privilege escalation, data exposure |
| Medium   | 4.0 - 6.9  | 1-2 weeks   | XSS, information disclosure |
| Low      | 0.1 - 3.9  | 2-4 weeks   | Minor information leaks |

### CVE Assignment

We request CVE identifiers for all confirmed security vulnerabilities, regardless of severity. This ensures:

- Complete transparency with our user community
- Proper tracking in vulnerability databases
- Clear communication about security impacts
- Compliance with enterprise security requirements

If you have already requested a CVE, please include the CVE-ID in your report. Otherwise, we will handle CVE assignment through our CNA (CVE Numbering Authority) process.

## Security-First Development

Range42 follows a security-first development approach:

### Security Practices

- **Secure by Design**: Security considerations integrated from initial design
- **Regular Security Reviews**: Code reviews with security focus
- **Automated Security Testing**: SAST, DAST, and dependency scanning
- **Minimal Attack Surface**: Principle of least privilege and minimal exposure
- **Defense in Depth**: Multiple layers of security controls

### Security Features

- **Network Isolation**: Proper network segmentation in training environments
- **Access Controls**: Role-based access control (RBAC)
- **Audit Logging**: Comprehensive logging of security-relevant events
- **Secure Communications**: TLS/SSL encryption for most communications
- **Input Validation**: Rigorous validation and sanitization of all inputs
- **Container Security**: Secure container configurations and image scanning

## Vulnerability Disclosure Policy

### Responsible Disclosure

We believe in responsible disclosure that balances:
- **User Safety**: Ensuring users can protect themselves
- **Researcher Recognition**: Acknowledging security researchers' contributions
- **Coordinated Timeline**: Allowing adequate time for fixes and deployment

### Public Disclosure Process

1. **Vulnerability Reported**: Initial report received and acknowledged
2. **Investigation**: Vulnerability validated and assessed
3. **Fix Development**: Patch developed and tested
4. **Pre-release**: Fix shared with reporter for verification
5. **Release**: Security update published
6. **Public Disclosure**: Advisory published with CVE details
7. **Recognition**: Researcher credited (if desired)

## Security Contact Information

- **Security Team**: [security@range42.net](mailto:security@range42.net)
- **General Inquiries**: [info@range42.net](mailto:info@range42.net)
- **Website**: [https://www.range42.net/security](https://www.range42.net/security)

---

*This security policy is reviewed and updated regularly. Last updated: 2025-07-10

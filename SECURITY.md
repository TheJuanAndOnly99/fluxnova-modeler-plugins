# Security Policy

This project supports responsible disclosure of security vulnerabilities and adheres to the [FINOS Security Vulnerabilities Responsible Disclosure Policy](https://community.finos.org/docs/governance/Software-Projects/cve-responsible-disclosure).

If you believe you have found a security vulnerability in this project, we encourage and appreciate your report. Please report it privately using one of the methods below — **do not** open a public GitHub Issue or otherwise disclose it publicly.

## Reporting a Vulnerability

- **GitHub private vulnerability reporting (preferred):** Use the ["Report a vulnerability"](https://github.com/finos/fluxnova-modeler-plugins/security/advisories/new) button under this repository's **Security** tab. This opens a private advisory and communication channel with the maintainers.
- **Email:** If you are unable to use GitHub's private reporting, email the [project maintainers](https://github.com/finos/fluxnova-modeler-plugins/blob/main/MAINTAINERS.md) directly and CC [security@finos.org](mailto:security@finos.org) with a description of the vulnerability.

Include the following in your report:
- Description of the vulnerability
- Steps to reproduce
- Potential impact
- Any relevant screenshots or logs

## Vulnerability Response Process

1. **Report the vulnerability privately** using one of the methods above. Do not create a public GitHub Issue.
2. **Acknowledgment:** The project team will acknowledge receipt of your report within **3 business days**.
3. **Triage:** The team will triage and investigate the issue within **7 days** of acknowledgment.
4. **Resolution:** If confirmed, the team will work with you to develop and test a fix. Target resolution times:
   - **Critical severity (CVSS 9.0+):** Fix released within **7 days**
   - **High severity (CVSS 7.0-8.9):** Fix released within **14 days**
   - **Medium severity (CVSS 4.0-6.9):** Fix released within **30 days**
   - **Low severity (CVSS 0.1-3.9):** Fix included in next scheduled release
5. **Disclosure:** Once a fix is available, the vulnerability will be publicly disclosed in accordance with the [FINOS Security Vulnerabilities Responsible Disclosure Policy](https://community.finos.org/docs/governance/Software-Projects/cve-responsible-disclosure).

## Supported Versions

Security updates are provided only for the latest release. See [SUPPORT.md](SUPPORT.md) for the complete support policy.

## Dependency and Code Scanning Policy

This section documents the project's policy for software composition analysis (SCA) and static application security testing (SAST) findings.

### Software Composition Analysis (SCA)

Two workflows enforce SCA policies, with separate concerns:

#### Vulnerability Scanning (`dependency-review`)

Runs on every pull request and blocks merging when a dependency with a known vulnerability or malicious package is added. Fails on **high severity or above**.

#### License Scanning (`license-scanning`)

Performs full dependency tree license scans using `license-checker-rseidelsohn`:
- Runs **weekly**, on **`workflow_dispatch`**, and on changes to `package.json`/`package-lock.json`
- Enforces **FINOS Category A licenses only**
- Release workflow requires license check to pass before publishing

**Allowed licenses (FINOS Category A):**
Apache-2.0, Apache-1.1, MIT, ISC, BSD-2-Clause, BSD-3-Clause, 0BSD, Unlicense, Python-2.0, PostgreSQL, BSL-1.0, W3C, WTFPL, Xnet, NCSA, ZPL-2.0, zlib, BlueOak-1.0.0, CC-BY-4.0 (data only).

**Excluded packages with documented justification:**
- `bpmn-js`: Reported as "Custom: LICENSE" but is MIT with a watermark visibility clause (permissive, Apache-2.0 compatible)

<!-- TODO: Enable Dependabot alerts and security updates in repository settings -->

#### SCA Remediation Thresholds

**Vulnerabilities:**
- Critical and high severity vulnerabilities in runtime dependencies must be fixed within **7 days** of being reported
- Medium severity vulnerabilities must be fixed within **30 days**
- Low severity vulnerabilities must be fixed in the next scheduled release

**Licenses:**
- Dependencies with licenses not in FINOS Category A must be removed or replaced before the change is merged
- License violations block releases via the `license-check` job in the release workflow

A vulnerability may be suppressed only when a maintainer determines it is non-exploitable for this project. The suppression must be:
- Documented in the OpenVEX file ([vex/fluxnova-modeler-plugins.openvex.json](vex/fluxnova-modeler-plugins.openvex.json))
- Accompanied by a written justification and re-review date
- Removed when the dependency is upgraded or the re-review date passes

### Static Application Security Testing (SAST)

<!-- TODO: Enable CodeQL default setup in repository settings -->

**SAST remediation thresholds:**
- Critical and high severity findings must be fixed before merge
- Medium and low severity findings must be fixed or dismissed with documented justification within **30 days**
- A finding may be dismissed only when it is declared a false positive or non-exploitable, with the reason recorded on the alert

### Pre-Release Requirements

All SCA findings above the thresholds documented in this policy must be addressed before any release. The release workflow will not publish assets that fail security checks.

## Verifying Release Integrity and Authenticity

Releases are produced by automated GitHub Actions workflows. No maintainer publishes a release from a personal machine.

### GitHub Releases

Each release includes:
- The plugin ZIP bundle (`code-editor-plugin-v{version}.zip`)
- A CycloneDX software bill of materials (`code-editor-plugin-v{version}.cdx.json`)
- Build provenance attestation via [actions/attest-build-provenance](https://github.com/actions/attest-build-provenance)
- SBOM attestation via [actions/attest-sbom](https://github.com/actions/attest-sbom)

### Verifying Attestations

To verify the build provenance and SBOM attestations for a release artifact:

```bash
# Install GitHub CLI if needed
# https://cli.github.com/

# Verify the artifact attestation
gh attestation verify code-editor-plugin-v{version}.zip \
  --repo finos/fluxnova-modeler-plugins
```

The attestation confirms:
- The artifact was built by the official release workflow in this repository
- The specific commit that produced the artifact
- The build environment and inputs

### Expected Release Identity

All official releases are:
- Built by GitHub Actions workflows in the `finos/fluxnova-modeler-plugins` repository
- Published via the `Release Workflow` (`.github/workflows/release.yml`)
- Signed using GitHub's artifact attestation infrastructure

If an artifact fails attestation verification, do not use it and report the issue to the maintainers.

## CRA Escalation (For Maintainers)

CRA stewardship: This project is supported under the Linux Foundation CRA stewardship framework. Security vulnerabilities should be reported through the mechanisms described in this file, which we will coordinate with our CRA steward. For actively exploited vulnerabilities and severe incidents that may require CRA escalation, please use the project's emergency security reporting mechanisms as appropriate. Read more at https://www.linuxfoundation.org/security .

**Project maintainers MUST escalate** the issue to the LF steward at [steward@linuxfoundation.org](mailto:steward@linuxfoundation.org) if the project experiences either of the following:

* **Actively exploited vulnerabilities:** a security vulnerability where the project has reliable evidence that a malicious actor has exploited it.
* **Severe incident:** a security compromise of the project's own IT infrastructure.

Ordinary vulnerabilities with no evidence of exploitation are not CRA escalation events. Escalate those that are actively exploited.

---

Thank you for helping keep FINOS projects and their users secure.

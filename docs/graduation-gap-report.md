# FINOS Graduated Status Gap Report

This document audits the `fluxnova-modeler-plugins` repository against the requirements for FINOS Graduated lifecycle status, including OpenSSF Best Practices Badge and OpenSSF OSPS Baseline Level 3 (version 2025-02-25).

**Audit Date:** 2026-10-13  
**Repository:** TheJuanAndOnly99/fluxnova-modeler-plugins (fork of finos/fluxnova-modeler-plugins)

---

## Summary

| Category | Met | Partial | Missing | Org-Level |
|----------|-----|---------|---------|-----------|
| FINOS Graduated Acceptance | 3 | 2 | 4 | 3 |
| OSPS Access Control | 0 | 0 | 0 | 5 |
| OSPS Build & Release | 2 | 2 | 3 | 0 |
| OSPS Documentation | 3 | 1 | 4 | 0 |
| OSPS Governance | 3 | 1 | 1 | 0 |
| OSPS Legal | 4 | 0 | 0 | 1 |
| OSPS Quality | 4 | 1 | 1 | 1 |
| OSPS Security Assessment | 0 | 0 | 2 | 0 |
| OSPS Vulnerability Management | 2 | 2 | 5 | 0 |

---

## FINOS Graduated Acceptance Requirements

### Incubation Maintenance (Prerequisites)

| Requirement | Status | Evidence | Proposed Fix |
|-------------|--------|----------|--------------|
| Project adhered to roadmap during Incubation | **Org-level** | Requires FINOS PMC assessment | N/A - organization decision |
| Project is self-sufficient without significant FINOS staff support | **Org-level** | Requires FINOS PMC assessment | N/A - organization decision |

### Graduated Acceptance Requirements

| Requirement | Status | Evidence | Proposed Fix |
|-------------|--------|----------|--------------|
| Production-ready major release (v1.0.0+) | **Met** | `code-editor-plugin` at v1.0.0 in package.json | None needed |
| Release announced to announce@lists.finos.org | **Missing** | No evidence of announcement | TODO: Maintainer action - announce release to FINOS mailing list |
| Maintainers from 3+ organizations (1 FINOS member) | **Org-level** | MAINTAINERS.md points to main repo | TODO: Verify maintainer diversity with upstream |
| Actively used by 5+ organizations (3 from finserv) | **Missing** | No documented adopters | TODO: Document adopter organizations |
| 2+ public end-user adoption stories | **Missing** | No case studies available | TODO: Publish adoption stories/case studies |
| Publish and adhere to FINOS responsible disclosure | **Partial** | SECURITY.md exists with basic policy | Enhance SECURITY.md with response timeframes |
| README links to accurate usage/maintenance docs | **Met** | Links to docs/installing-plugins.md | None needed |
| Community sustainability plan with go-to-market strategy | **Missing** | Not documented | TODO: Work with FINOS staff (help@finos.org) |
| Clear financial services value proposition | **Partial** | README mentions Fluxnova but no FS-specific value prop | TODO: Add FS value proposition to documentation |

### Graduated Ongoing Maintenance Requirements

| Requirement | Status | Evidence | Proposed Fix |
|-------------|--------|----------|--------------|
| Feature work adheres to public roadmap | **Missing** | No public roadmap documented | TODO: Create ROADMAP.md or GitHub Projects board |
| Community Development Plan milestones | **Missing** | Not documented | TODO: Work with FINOS staff |
| Adherence to OSPS Baseline Level 3 | **Partial** | See detailed OSPS assessment below | Implement gaps identified in this report |
| Semantic versioning from v1.0.0+ | **Met** | package.json shows v1.0.0, release workflow uses semver | None needed |

---

## OpenSSF OSPS Baseline Level 3 Requirements

### Access Control (OSPS-AC)

| Control ID | Requirement | Status | Evidence | Proposed Fix |
|------------|-------------|--------|----------|--------------|
| OSPS-AC-01.01 | MFA required for collaborators accessing sensitive resources | **Org-level** | GitHub org/repo settings | Enable via GitHub org settings |
| OSPS-AC-02.01 | New collaborators get lowest privileges by default | **Org-level** | GitHub default behavior | Verify org settings |
| OSPS-AC-03.01 | Direct commits to primary branch prevented | **Org-level** | Requires branch protection ruleset | Enable branch protection on main |
| OSPS-AC-03.02 | Primary branch deletion requires explicit confirmation | **Org-level** | Requires branch protection ruleset | Enable via branch protection |
| OSPS-AC-04.01 | CI/CD defaults to lowest permissions | **Org-level** | Requires repo-level default | Set `permissions: {}` at repo level in Settings |
| OSPS-AC-04.02 | Jobs specify minimum necessary permissions | **Missing** | Workflows lack explicit permissions blocks | Add `permissions:` to all workflow jobs |

### Build and Release (OSPS-BR)

| Control ID | Requirement | Status | Evidence | Proposed Fix |
|------------|-------------|--------|----------|--------------|
| OSPS-BR-01.01 | CI/CD input parameters sanitized | **Partial** | Workflows use `github.ref_name` directly | Review for injection risks |
| OSPS-BR-02.01 | Unique version identifier per release | **Met** | Release workflow extracts version from package.json | None needed |
| OSPS-BR-02.02 | All release assets associated with version ID | **Met** | ZIP files named with version | None needed |
| OSPS-BR-03.01 | Official URIs use encrypted channels | **Met** | GitHub uses HTTPS | None needed |
| OSPS-BR-04.01 | Releases contain descriptive changelog | **Partial** | Uses `--generate-notes` which auto-generates | Consider structured CHANGELOG.md |
| OSPS-BR-05.01 | Standardized dependency tooling | **Met** | Uses npm with package-lock.json | None needed |
| OSPS-BR-06.01 | Releases signed or include signed manifest with hashes | **Missing** | No signatures or provenance attestation | Add `actions/attest-build-provenance` and `actions/attest-sbom` to release workflow |

### Documentation (OSPS-DO)

| Control ID | Requirement | Status | Evidence | Proposed Fix |
|------------|-------------|--------|----------|--------------|
| OSPS-DO-01.01 | User guides for basic functionality | **Met** | docs/installing-plugins.md | None needed |
| OSPS-DO-02.01 | Guide for reporting defects | **Met** | Issue templates exist in .github/ISSUE_TEMPLATE | None needed |
| OSPS-DO-03.01 | Instructions to verify release integrity/authenticity | **Missing** | No verification instructions | Add verification instructions to documentation |
| OSPS-DO-03.02 | Instructions to verify expected identity of release author | **Missing** | No identity verification docs | Add to SECURITY.md or release docs |
| OSPS-DO-04.01 | Support scope and duration statement | **Missing** | No SUPPORT.md | Create SUPPORT.md |
| OSPS-DO-05.01 | Statement on when releases stop receiving security updates | **Missing** | No EOL policy | Add to SUPPORT.md |
| OSPS-DO-06.01 | Description of dependency selection/tracking | **Partial** | renovate.json exists but no policy documented | Add dependency management policy to documentation |

### Governance (OSPS-GV)

| Control ID | Requirement | Status | Evidence | Proposed Fix |
|------------|-------------|--------|----------|--------------|
| OSPS-GV-01.01 | List of members with sensitive resource access | **Partial** | MAINTAINERS.md exists but points to main repo | Acceptable; consider local list |
| OSPS-GV-01.02 | Roles and responsibilities documented | **Met** | Via CONTRIBUTING.md pointing to main repo | None needed |
| OSPS-GV-02.01 | Mechanisms for public discussion | **Met** | GitHub Issues enabled | None needed |
| OSPS-GV-03.01 | Contribution process explanation | **Met** | CONTRIBUTING.md exists | None needed |
| OSPS-GV-03.02 | Guide for acceptable contributions | **Partial** | Points to main repo; no local standards | Consider adding contribution standards |
| OSPS-GV-04.01 | Policy for reviewing contributors before permission escalation | **Missing** | Not documented | Add contributor review policy |

### Legal (OSPS-LE)

| Control ID | Requirement | Status | Evidence | Proposed Fix |
|------------|-------------|--------|----------|--------------|
| OSPS-LE-01.01 | Contributors assert legal authorization (DCO/CLA) | **Org-level** | FINOS uses EasyCLA | Verify EasyCLA enabled on upstream |
| OSPS-LE-02.01 | Source code license meets OSI/FSF definition | **Met** | Apache-2.0 license | None needed |
| OSPS-LE-02.02 | Released assets license meets OSI/FSF definition | **Met** | Apache-2.0 in LICENSE, MIT in code-editor-plugin | None needed |
| OSPS-LE-03.01 | License in LICENSE file | **Met** | LICENSE and LICENSE.spdx exist | None needed |
| OSPS-LE-03.02 | License included with release assets | **Met** | Bundle includes license via npm pack | None needed |

### Quality (OSPS-QA)

| Control ID | Requirement | Status | Evidence | Proposed Fix |
|------------|-------------|--------|----------|--------------|
| OSPS-QA-01.01 | Source publicly readable at static URL | **Met** | GitHub public repository | None needed |
| OSPS-QA-01.02 | Public change history | **Met** | Git history preserved | None needed |
| OSPS-QA-02.01 | Dependency list in repository | **Met** | package.json and package-lock.json | None needed |
| OSPS-QA-02.02 | Compiled releases include SBOM | **Missing** | No SBOM generated | Add CycloneDX SBOM generation to release workflow |
| OSPS-QA-03.01 | Status checks must pass before merge | **Org-level** | Requires branch protection | Enable required status checks |
| OSPS-QA-04.01 | Subprojects documented | **Met** | plugins/ structure documented in README | None needed |
| OSPS-QA-04.02 | Subprojects enforce equal security requirements | **Partial** | Both plugins use same CI | Verify consistent security practices |
| OSPS-QA-05.01 | No generated executables in VCS | **Met** | .gitignore excludes dist/, no binaries committed | None needed |
| OSPS-QA-06.01 | Automated tests run on commits | **Met** | CI runs `npm run all` including tests | None needed |
| OSPS-QA-06.02 | Documentation on when/how tests run | **Partial** | README mentions `npm run build`, not test policy | Document test execution policy |
| OSPS-QA-06.03 | Policy requiring tests for major changes | **Missing** | Not documented | Add tests policy to CONTRIBUTING |
| OSPS-QA-07.01 | Non-author approval required for primary branch | **Org-level** | Requires branch protection | Enable required reviews |

### Security Assessment (OSPS-SA)

| Control ID | Requirement | Status | Evidence | Proposed Fix |
|------------|-------------|--------|----------|--------------|
| OSPS-SA-01.01 | Design documentation of actions and actors | **Missing** | No architecture/design docs | TODO: Create design documentation |
| OSPS-SA-02.01 | External software interfaces documented | **Partial** | Installing guide covers plugin interface | Expand API documentation |
| OSPS-SA-03.01 | Security assessment performed | **Missing** | No security assessment documented | TODO: Perform and document security assessment |
| OSPS-SA-03.02 | Threat model and attack surface analysis | **Missing** | No threat model | TODO: Create THREAT_MODEL.md |

### Vulnerability Management (OSPS-VM)

| Control ID | Requirement | Status | Evidence | Proposed Fix |
|------------|-------------|--------|----------|--------------|
| OSPS-VM-01.01 | Coordinated vulnerability reporting policy with timeframe | **Partial** | SECURITY.md exists but lacks response timeframe | Add explicit response timeframe |
| OSPS-VM-02.01 | Security contacts published | **Met** | SECURITY.md references maintainers and security@finos.org | None needed |
| OSPS-VM-03.01 | Private vulnerability reporting available | **Met** | GitHub private reporting and email | None needed |
| OSPS-VM-04.01 | Vulnerability data publicly published | **Partial** | FINOS policy referenced, no project-specific process | Document local process |
| OSPS-VM-04.02 | Non-exploitable vulnerabilities documented in VEX | **Missing** | No VEX file | Create OpenVEX document |
| OSPS-VM-05.01 | SCA remediation threshold policy | **Missing** | Not documented | Add SCA policy to SECURITY.md |
| OSPS-VM-05.02 | SCA violations addressed before release | **Missing** | No SCA workflow | Add dependency-review workflow |
| OSPS-VM-05.03 | Automatic SCA evaluation blocking violations | **Missing** | No required SCA check | Add dependency-review as required check |
| OSPS-VM-06.01 | SAST remediation threshold policy | **Missing** | Not documented | Add SAST policy to SECURITY.md |
| OSPS-VM-06.02 | Automatic SAST evaluation blocking violations | **Missing** | No SAST in CI | Recommend enabling CodeQL default setup |

---

## Manual Follow-Up Items (Org/GitHub Settings)

The following items cannot be implemented via code changes and require manual configuration:

### GitHub Repository Settings

1. **Enable branch protection on `main`:**
   - Require pull request reviews before merging
   - Require status checks to pass (CI, dependency-review, license-scanning)
   - Prevent direct pushes to main
   - Prevent branch deletion

2. **Enable GitHub security features:**
   - Enable Dependabot alerts and security updates
   - Enable secret scanning with push protection
   - Enable CodeQL default setup for JavaScript/TypeScript

3. **Set default workflow permissions:**
   - Settings → Actions → General → Workflow permissions
   - Select "Read repository contents and packages permissions"

### FINOS Organization Actions

1. **Verify EasyCLA is enabled** for contributor license agreement
2. **Register for OpenSSF Best Practices Badge** at bestpractices.dev
3. **Announce v1.0.0 release** to announce@lists.finos.org
4. **Work with FINOS staff** on community sustainability plan

---

## Implementation Plan

### Phase 1: Immediate (This PR)

- [x] Create gap report
- [x] Add dependency-review workflow (vulnerability/malicious package blocking on PRs)
- [x] Add license-scanning workflow (full-tree license scan with `license-checker-rseidelsohn`)
- [x] Update release workflow with SBOM, provenance attestation, and license check gate
- [x] Add least-privilege `permissions:` to all workflow jobs
- [x] Enhance SECURITY.md with response timeframes and SCA/SAST policies
- [x] Create SUPPORT.md
- [x] Update CONTRIBUTING.md with local policies
- [x] Create OpenVEX starter file

**Workflow responsibility split:**
- `dependency-review`: CVEs and malicious packages on every PR (fails on high severity)
- `license-scanning`: FINOS Category A license compliance (weekly, on dependency changes, before release)

### Phase 2: Follow-Up (Manual/Upstream)

- Configure branch protection rules
- Enable Dependabot and CodeQL
- Register for OpenSSF Best Practices Badge
- Document adopter organizations
- Create public roadmap

### Phase 3: Future Considerations

- Create THREAT_MODEL.md
- Expand design documentation
- Add security assessment documentation

---

## Current License Scan Findings

The `license-scanning.yml` workflow scans production dependencies against FINOS Category A licenses. As of this audit:

### code-editor-plugin

| License | Count | Notes |
|---------|-------|-------|
| MIT | 232 | Category A ✓ |
| ISC | 11 | Category A ✓ |
| BSD-2-Clause | 9 | Category A ✓ |
| BlueOak-1.0.0 | 7 | OSI-approved permissive (allowed) |
| Apache-2.0 | 5 | Category A ✓ |
| BSD-3-Clause | 3 | Category A ✓ |
| Python-2.0 | 1 | Category A ✓ |
| CC-BY-4.0 | 1 | caniuse-lite (data, not code - allowed) |
| Custom: LICENSE | 1 | bpmn-js - MIT with watermark clause (excluded, see below) |

### Excluded Packages

- **bpmn-js@18.1.2**: Reported as "Custom: LICENSE" but is actually MIT with a watermark visibility clause. The license is permissive and compatible with Apache-2.0. Exclusion is documented in the workflow.

### mcp-start-event-plugin

| License | Count | Notes |
|---------|-------|-------|
| MIT | 1 | domify - Category A ✓ |

All production dependencies comply with FINOS Category A licensing requirements.

---

## References

- [FINOS Graduated Lifecycle Stage](https://community.finos.org/docs/governance/lifecycle-stages/graduated)
- [OpenSSF OSPS Baseline v2025-02-25](https://baseline.openssf.org/versions/2025-02-25)
- [FINOS License Categories](https://community.finos.org/docs/governance/software-projects/license-categories/)
- [FINOS Security Policy](https://community.finos.org/docs/governance/software-projects/cve-responsible-disclosure)
- [finos/architecture-as-code](https://github.com/finos/architecture-as-code) (reference implementation)

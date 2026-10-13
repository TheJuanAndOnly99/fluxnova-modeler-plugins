# Support

This page describes what support the Fluxnova Modeler Plugins project provides, which releases are supported, and when a release stops receiving security updates.

## Getting Help

Support is provided by the community on a best-effort basis. There is no service-level agreement.

- **Questions and usage help:** Open a [Support Question](https://github.com/finos/fluxnova-modeler-plugins/issues/new?template=support_question.yml) issue.
- **Bugs:** Open a [Bug Report](https://github.com/finos/fluxnova-modeler-plugins/issues/new?template=bug_report.yml).
- **Feature requests:** Open a [Feature Request](https://github.com/finos/fluxnova-modeler-plugins/issues/new?template=feature_request.yml).
- **Security vulnerabilities:** Do not open a public issue. Follow [SECURITY.md](SECURITY.md).
- **General FINOS questions:** Email [help@finos.org](mailto:help@finos.org).

<!-- TODO: Add project mailing list or community meeting links when available -->

## Supported Releases

**Only the latest published release of each plugin is supported.** Bug fixes and security fixes are delivered by publishing a new release, not by patching older versions.

| Plugin | Distribution | Supported Version |
|--------|--------------|-------------------|
| code-editor-plugin | [GitHub Releases](https://github.com/finos/fluxnova-modeler-plugins/releases) | Latest release only |
| mcp-start-event-plugin | [GitHub Releases](https://github.com/finos/fluxnova-modeler-plugins/releases) | Latest release only |

<!-- TODO: Update this table as additional plugins are released -->

## When a Release Stops Receiving Security Updates

A release stops receiving security updates **at the moment a newer release of the same plugin is published**. Security fixes are always released as a new version. If you are on an older version, upgrade to the latest release to receive the fix.

Pre-releases (for example `-rc`, `-beta`, or `-alpha` versions) are not supported and receive no security updates.

## End-of-Life Policy

<!-- TODO: Define specific EOL policy when project matures -->

The project does not currently maintain long-term support (LTS) branches. When the project decides to end support for a major version line:

1. The end-of-life date will be announced at least **90 days** in advance
2. The announcement will be made via:
   - A notice in the README
   - A GitHub Discussion or Issue
   - The FINOS mailing list (if applicable)
3. After the EOL date, the version will no longer receive security updates

## Versioning

This project follows [Semantic Versioning](https://semver.org/):

- **MAJOR** version increments indicate incompatible API changes
- **MINOR** version increments indicate new functionality in a backwards-compatible manner
- **PATCH** version increments indicate backwards-compatible bug fixes

Breaking changes are documented in release notes and any necessary migration guidance is provided.

## Compatibility

<!-- TODO: Document Fluxnova Modeler version compatibility when known -->

| Plugin Version | Fluxnova Modeler Version | Node.js Version |
|----------------|--------------------------|-----------------|
| 1.x | TBD | 24.x |

## Reporting Issues

When reporting issues, please include:

1. Plugin name and version
2. Fluxnova Modeler version
3. Operating system and version
4. Steps to reproduce the issue
5. Expected vs actual behavior
6. Any relevant error messages or logs

---

For security vulnerabilities, please follow the process described in [SECURITY.md](SECURITY.md).

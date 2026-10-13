# Security Policy

Forge components are meant to be reused as infrastructure. Security is a first-class requirement, not a follow-up.

## Supported versions

This repository is pre-1.0 and evolving component by component. Each component README states its own readiness and support status. Assume anything without an explicit readiness statement is **not** production-ready.

## Reporting a vulnerability

- **Do not** open a public issue for a suspected vulnerability.
- Open a private security advisory on GitHub, or contact the maintainer directly.
- Include: component + version/commit, reproduction steps, impact, and any suggested mitigation.

You can expect acknowledgment within 72 hours and a fix timeline based on severity.

## Security expectations for components

- Validate all untrusted input at the boundary; fail closed with predictable errors.
- Secure defaults; secrets via environment / secret manager, never hardcoded.
- Least privilege for credentials, tokens, and storage access.
- No custom cryptography. Use vetted libraries and document the choice.
- Timeouts on all I/O; safe retry behavior; no secret leakage in logs or errors.
- Document threat model, trust boundaries, and known limitations in the component README.

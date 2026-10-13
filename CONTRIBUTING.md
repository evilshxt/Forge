# Contributing to Forge

Forge grows one component at a time. This file is the short contract for adding one well.

## Before you build

1. Check open issues / existing components — no duplicates without reason.
2. Define the problem in one paragraph: who reuses this, and what pain does it remove?
3. Define non-goals explicitly. What will this component **not** do?
4. State the runtime, language, and dependencies. New stack needs justification.
5. State security + reliability requirements relevant to the domain.

If any of the above is ambiguous and blocks safe progress, ask before implementing.

## Build rules

- Smallest complete version first. No premature adapters, no hypothetical providers.
- Follow the existing conventions of the repo (naming, formatting, testing).
- Explicit contracts: config, inputs/outputs, error behavior.
- Secure defaults. Validate untrusted input. No hardcoded secrets — provide `.env.example`-style safe examples only.
- Reliability: timeouts, cleanup, graceful shutdown, safe retries (backoff + jitter, no retry storms, no unsafe duplicates).
- Observability where it helps: structured logs, correlation IDs, health checks, metrics.
- Never reinvent crypto. Use vetted libraries.
- Never swallow errors, fake success, or use unbounded retries.
- Never weaken security to make tests pass.

## Definition of done

- [ ] Implementation matches the stated scope
- [ ] Tests cover happy path **and** meaningful failure paths (invalid input, timeouts, retries, cleanup)
- [ ] `README.md` in the component dir follows `docs/component-template.md`
- [ ] Limitations + readiness status documented honestly
- [ ] Verified from a clean setup (fresh clone / fresh install, per the README steps)
- [ ] No unrelated changes, no silent interface changes, no stray secrets

## Pull requests

- One component or one focused fix per PR.
- Description states: problem, scope, trade-offs, what was tested and how.
- Do not claim tests / benchmarks / security checks passed unless they were actually run — paste the command + result.

## AI agent notes

- Inspect repo structure, docs, and manifests before writing code.
- Don't introduce layers or dependencies without stating why.
- Keep docs aligned with actual behavior.
- Prefer verifiable implementation over scaffolding.

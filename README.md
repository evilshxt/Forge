# Forge

Reusable, production-grade internal systems, infrastructure components, and developer utilities.

Forge exists to solve common engineering problems properly once — then reuse the solutions instead of rebuilding infrastructure from scratch for every new project.

> **Core principle:** Build infrastructure that future projects can confidently reuse. Keep it focused, verify its behavior, document its limitations, and earn the word "production-grade."

---

## What this is

A long-term, evolving collection of focused building blocks for the systems behind modern applications:

- **Communication** — email delivery, templates, queues, webhooks, notifications
- **Observability** — structured logging, correlation, metrics, health checks, audit logging
- **Reliability** — retries with backoff + jitter, timeouts, circuit breakers, rate limiting, idempotency, queues, schedulers, locks
- **Security** — sessions, JWT / API keys, RBAC, encryption wrappers, secrets config, validation
- **Data & storage** — DB adapters, migrations, caching, object-storage adapters, file processing
- **Developer utilities** — PDF/CSV, images, QR codes, API clients, config validation, feature flags

Forge is **not** a single app, a SaaS product, or a set of toy demos. Each system is developed, tested, documented, and integrated independently.

## What this is not (yet)

This repository is intentionally starting small. There are no placeholder modules or empty packages here. Components land one at a time, only when they are scoped, implemented, tested, and documented.

## Engineering principles

1. **Security by design.** Validate untrusted input, protect secrets, least privilege, explicit security-sensitive behavior.
2. **Reliability over appearances.** Timeouts, partial failures, retries, duplicates, cleanup, shutdown.
3. **Observable by default.** Structured logs, error context, health checks, metrics — where they genuinely help.
4. **Small, cohesive components.** One clear responsibility, no unnecessary abstraction.
5. **Explicit contracts.** Interfaces, config, errors, inputs/outputs defined up front.
6. **Test failure paths.** Edge cases, invalid input, timeouts, retries — not just happy paths.
7. **Document integration.** Every component shows how another app configures and uses it.
8. **Honest readiness.** No "production-ready" claims without evidence. State what was and wasn't tested.
9. **Justified dependencies.** A dependency must earn its maintenance and security cost.
10. **No unnecessary complexity.** No microservices, containers, dashboards, or frameworks without a concrete reason.

Additional rules:

- Never reinvent cryptography — use vetted libraries.
- Never hardcode credentials or weaken security to make tests pass.
- No unbounded retries, no swallowed errors, no faked successes.

## Repository structure

```text
forge/
├── README.md
├── LICENSE
├── CONTRIBUTING.md
├── SECURITY.md
├── docs/
│   ├── component-template.md          # template for new component READMEs
│   └── production-readiness-checklist.md
└── <component>/                       # one directory per system, added incrementally
    ├── README.md                      # purpose, non-goals, usage, limits, readiness
    ├── src/ (or runtime-appropriate layout)
    └── tests/
```

No shared monolith, no forced common database, no premature abstraction. If a component depends on another Forge component, that dependency is documented explicitly.

## Workflow: one component at a time

1. Define the problem and what's **out of scope**.
2. Identify runtime, language, interfaces, dependencies.
3. Define security + reliability requirements.
4. Implement the smallest complete version.
5. Add tests, including failure cases.
6. Add a concise `README.md` with setup + usage.
7. Document limitations and readiness status.
8. Verify from a clean setup.

See [CONTRIBUTING.md](./CONTRIBUTING.md) and [docs/component-template.md](./docs/component-template.md).

## Production-readiness expectations

Per component, where relevant:

- Clear API + config contracts, secure defaults
- Input validation, predictable errors
- Timeouts, cleanup, graceful shutdown
- Retry behavior that avoids storms and unsafe duplicates
- Structured logging, correlation IDs, metrics, health checks
- Unit + integration tests
- Dependency + config docs, practical examples
- Known limitations, deployment notes

Full list: [docs/production-readiness-checklist.md](./docs/production-readiness-checklist.md).

Not every item applies to every component. When one doesn't, the component README says why.

## Reuse philosophy

Prefer stable interfaces and adapters **when a real use case demands them** — e.g. SMTP now, another email provider later; local storage now, S3-compatible later; in-memory queue for tests, Redis-backed for production.

But: no abstractions for hypothetical futures. Start with the smallest useful implementation.

## Status

| Area | Status |
| ---- | ------ |
| Repository | Foundation — no components yet |
| First component | TBD — chosen based on real project need |

Components will each carry their own readiness statement. Nothing here claims to be production-ready until it proves it.

## License

MIT — see [LICENSE](./LICENSE). Reuse freely, verify before trusting.

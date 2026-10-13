# Production-Readiness Checklist

Apply per component. Check what applies; justify what doesn't.

## Contract

- [ ] Clear API + config reference
- [ ] Predictable error behavior, documented error cases
- [ ] Versioned interface or explicit stability note

## Security

- [ ] Untrusted input validated at the boundary
- [ ] Secure defaults, no hardcoded secrets
- [ ] Least-privilege credentials
- [ ] Vetted crypto libraries only (no custom primitives)
- [ ] No secrets in logs / errors / examples

## Reliability

- [ ] Timeouts on all I/O
- [ ] Retry policy with backoff + jitter, no retry storms
- [ ] Idempotency or documented duplicate behavior
- [ ] Resource cleanup + graceful shutdown

## Observability

- [ ] Structured logs with useful context
- [ ] Correlation / request IDs where applicable
- [ ] Health / readiness checks where applicable
- [ ] Metrics where applicable

## Testing

- [ ] Unit tests for core logic
- [ ] Failure-path tests (invalid input, timeouts, retries, shutdown)
- [ ] Integration test against real dependency (or documented reason for fakes)
- [ ] Verified from a clean setup

## Documentation

- [ ] Purpose + non-goals
- [ ] Setup + minimal runnable example
- [ ] Limitations + deployment considerations
- [ ] Honest readiness statement (scope-specific, evidence-backed)

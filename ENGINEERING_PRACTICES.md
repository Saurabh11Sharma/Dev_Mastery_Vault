# Engineering Practices — Quality, Security & Delivery

## Testing strategy

Use a test pyramid as a guide, not a rigid ratio.

- Unit: business rules and pure functions; fast and deterministic.
- Integration: real database, queue or adapter behaviour where it matters.
- Contract: compatibility between independently developed components.
- End-to-end: a small number of critical user journeys.

Tests should verify observable behaviour, not implementation details. Include edge cases, invalid input, permission failures, concurrency and failure paths.

## Code review checklist

- Does the change solve the stated problem?
- Are business rules represented in the right layer?
- Are names and module boundaries clear?
- Is input validated at trust boundaries?
- Are authorisation checks object-aware?
- Are errors handled without leaking internals?
- Are database queries bounded and indexed appropriately?
- Are retries and side effects safe?
- Are tests meaningful and deterministic?
- Are logs useful but free of secrets and sensitive data?
- Is documentation updated where behaviour or setup changed?

## CI/CD pipeline baseline

1. Install dependencies reproducibly.
2. Run formatting or lint checks.
3. Run type checking.
4. Run unit and integration tests.
5. Build the application.
6. Scan dependencies and container images.
7. Publish immutable build artefacts.
8. Deploy through environment-specific approvals and configuration.
9. Run smoke checks and support rollback.

## Observability

Logs explain individual events. Metrics show trends and system health. Traces connect work across service boundaries. Use correlation IDs. Monitor latency percentiles, traffic, errors and saturation. Alerts should be actionable and tied to user impact.

## Security baseline

- Validate and normalise external input.
- Enforce authentication and resource-level authorisation.
- Store passwords using a suitable password-hashing algorithm.
- Protect cookies and tokens; define expiry, rotation and revocation.
- Use parameterised database access.
- Apply rate limits and request-size limits.
- Protect against SSRF, XSS, CSRF, injection and insecure direct object references.
- Keep dependencies and runtime versions maintained.
- Store secrets in a secret manager.
- Avoid exposing internal errors, stack traces or sensitive data.

References: [OWASP Top 10](https://owasp.org/www-project-top-ten/), [OWASP Cheat Sheet Series](https://cheatsheetseries.owasp.org/).

## Production readiness review

- What happens when the database is unavailable?
- What happens when a dependency is slow?
- Can the operation safely be retried?
- How do we detect and investigate failure?
- How do we roll back?
- What data is backed up and how is restore tested?
- What are the resource limits and expected costs?
- Who owns the service and its alerts?
- Is there a runbook for common incidents?

## Technical leadership

- Explain the problem and constraints before proposing a solution.
- Invite alternatives and compare trade-offs.
- Record important decisions in ADRs.
- Keep code reviews specific, respectful and actionable.
- Mentor through pairing, examples and feedback.
- Break delivery into demonstrable increments.
- Surface risks early and communicate impact clearly.
- Use retrospectives to improve the system, not assign blame.

## Useful references

- [Google Engineering Practices](https://google.github.io/eng-practices/)
- [Google SRE Book](https://sre.google/sre-book/table-of-contents/)
- [OWASP Cheat Sheet Series](https://cheatsheetseries.owasp.org/)
- [GitHub Actions Documentation](https://docs.github.com/en/actions)

# Node.js & TypeScript — Engineering Notes

## Node.js runtime mental model

Node.js runs JavaScript on V8 and uses libuv to support asynchronous I/O. JavaScript execution is primarily single-threaded per isolate, while the runtime uses operating-system facilities and a worker pool for selected operations.

- Call stack: currently executing JavaScript frames.
- Event loop: coordinates callbacks and asynchronous work.
- Microtasks: promise reactions and queueMicrotask callbacks.
- Timers: callbacks become eligible after a threshold; timing is not exact.
- Worker threads: useful for CPU-intensive JavaScript workloads, not a default I/O solution.
- Streams: process data incrementally and support backpressure.

Avoid blocking the event loop with expensive synchronous computation or large synchronous file operations in request paths.

## Asynchronous programming

Use async / await for readable control flow. Use Promise.all when tasks are independent and every result is required. Use Promise.allSettled when partial success is useful. Apply concurrency limits when processing large collections; launching thousands of promises at once can exhaust resources.

## Error handling

- Distinguish expected business errors from unexpected failures.
- Translate infrastructure errors at application boundaries.
- Do not return stack traces or internal database details to clients.
- Log enough context to investigate, but never log secrets or sensitive payloads.
- Preserve causal information when wrapping errors.
- Handle rejected promises and process-level failures deliberately.

## API trust boundaries

Treat every external value as untrusted: JSON bodies, query parameters, headers, webhooks and legacy database records.

A robust request path usually includes authentication, resource-level authorisation, runtime validation, application use case, domain invariants, persistence or external adapter, and response mapping.

TypeScript compile-time types do not validate incoming JSON. Use runtime schemas or DTO validation.

## TypeScript design

Prefer strict compiler settings. Use unknown at untrusted boundaries and narrow it. Avoid spreading any through application layers.

Use discriminated unions for state machines. They make state-specific data explicit and allow exhaustive handling. Keep DTOs, domain types and persistence models separate when their responsibilities differ.

## Security checklist

- Hash passwords with a suitable password-hashing algorithm such as Argon2id or bcrypt.
- Use TLS in production.
- Use secure, HttpOnly and appropriate SameSite cookie settings.
- Validate JWT issuer, audience, expiry and signature; define key rotation.
- Enforce object-level authorisation, not just route-level roles.
- Apply rate limits and request-size limits.
- Keep secrets in a secret manager or protected environment configuration.
- Prevent SSRF, injection and unsafe deserialisation.
- Keep dependencies updated.

## Testing layers

- Unit tests for pure functions and domain rules.
- Integration tests for adapters and database behaviour.
- HTTP tests for routing, validation and response contracts.
- Contract tests for service-to-service assumptions.
- End-to-end tests for critical user journeys.

## Further reading

- [Node.js Learn](https://nodejs.org/en/learn)
- [Node.js API](https://nodejs.org/api/)
- [TypeScript Handbook](https://www.typescriptlang.org/docs/handbook/intro.html)
- [NestJS Documentation](https://docs.nestjs.com/)
- [OWASP Cheat Sheet Series](https://cheatsheetseries.owasp.org/)

# Senior / Lead JavaScript & TypeScript Engineer — Learning Roadmap

An ordered, long-term curriculum focused on the skills used to design, build, test, deploy and operate production software.

## 1. JavaScript language and runtime

- Execution context, lexical scope, closures and the scope chain.
- this, prototypes, prototype chain, classes and inheritance.
- Primitive vs reference values, coercion, equality and immutability.
- Higher-order functions, composition, iterators and generators.
- Promises, async/await, error propagation and cancellation.
- Event loop, call stack, microtasks, timers and I/O callbacks.
- ESM vs CommonJS, package resolution and module boundaries.
- Memory, garbage collection and common memory leaks.

Practice: implement debounce, throttle, memoization, an event emitter, a promise utility and a concurrency-limited task runner. Explain edge cases and complexity.

Resources: [MDN JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript), [You Don't Know JS Yet](https://github.com/getify/You-Dont-Know-JS).

## 2. TypeScript for large applications

- Type inference, narrowing, unions, intersections and discriminated unions.
- Generics, constraints, conditional and mapped types.
- keyof, typeof, indexed access and utility types.
- Structural typing, assignability and strict compiler settings.
- unknown, never and any; runtime validation at trust boundaries.
- Domain types, DTOs, persistence models and API contracts.
- Package boundaries, declaration files and type-safe public APIs.

Practice: model an order/payment lifecycle with discriminated unions; create generic pagination and result types; validate external input at runtime.

Resource: [TypeScript Handbook](https://www.typescriptlang.org/docs/handbook/intro.html).

## 3. Node.js backend engineering

- V8, libuv, event-loop phases, worker threads and child processes.
- Streams, backpressure and large-file processing.
- HTTP lifecycle, REST design, pagination, filtering and versioning.
- Authentication vs authorisation; sessions, cookies, JWT and OAuth 2.0 / OIDC.
- Validation, error handling, configuration and graceful shutdown.
- Structured logging, metrics, tracing and correlation IDs.
- Rate limits, timeouts, idempotency, retries and circuit breakers.
- Background jobs, webhooks and scheduled work.

Practice: build a TypeScript API with authentication, RBAC, OpenAPI, logging, health checks, integration tests and Docker.

Resources: [Node.js Learn](https://nodejs.org/en/learn), [Node.js API](https://nodejs.org/api/), [NestJS Docs](https://docs.nestjs.com/).

## 4. PostgreSQL and data engineering

- Relational modelling, normalisation, keys and constraints.
- Joins, subqueries, CTEs, aggregates and window functions.
- Transactions, ACID, isolation levels, locks and deadlocks.
- B-tree, composite, partial, expression and GIN indexes.
- EXPLAIN ANALYZE, query plans and performance investigation.
- Offset vs keyset pagination, connection pooling and migrations.
- Backups, restore testing and least-privilege access.

Practice: model customers, orders, inventory and payments; add constraints and indexes; compare query plans before and after optimisation.

Resources: [PostgreSQL Docs](https://www.postgresql.org/docs/current/), [Use The Index, Luke](https://use-the-index-luke.com/).

## 5. React and Next.js

- Components, props, state, rendering and reconciliation.
- Hooks, effects, refs, context, forms and component composition.
- Data fetching, caching, optimistic updates and error states.
- Server-side rendering, static generation and streaming.
- Next.js App Router, Server Components and secure data access.
- Accessibility, bundle analysis, lazy loading and Core Web Vitals.
- Unit, component and end-to-end testing.

Resources: [React Learn](https://react.dev/learn), [Next.js Docs](https://nextjs.org/docs).

## 6. Architecture and design

- Cohesion, coupling, dependency direction and information hiding.
- SOLID as design heuristics, not rules to apply mechanically.
- Layered, Hexagonal / Ports-and-Adapters and Clean Architecture.
- DDD: ubiquitous language, entities, value objects, aggregates, repositories and domain events.
- Bounded contexts, modular monoliths and service boundaries.
- CQRS when read/write models genuinely differ.
- Event-driven architecture, transactional outbox and sagas.
- API contracts, schema evolution, ADRs and C4 diagrams.

Practice: implement a business capability behind ports and adapters; document the persistence and messaging decisions in ADRs.

## 7. Distributed systems and microservices

- Partial failure, network timeouts and latency.
- At-most-once, at-least-once and effectively-once processing.
- Idempotent consumers, deduplication and message ordering.
- Queues, topics, pub/sub and dead-letter queues.
- Exponential backoff, jitter, retry budgets and circuit breakers.
- Sagas, orchestration vs choreography and transactional outbox.
- Consistency, replication, partitioning and CAP trade-offs.
- Observability across service boundaries.

Resources: [Designing Data-Intensive Applications](https://dataintensive.net/), [Microservices.io](https://microservices.io/).

## 8. AWS and DevOps

- IAM roles and policies, VPC, subnets and security groups.
- EC2, S3, RDS, Lambda, API Gateway, SQS, SNS and EventBridge.
- Step Functions, CloudWatch, CloudTrail and Secrets Manager.
- Serverless cold starts, concurrency, quotas and database connections.
- Docker, multi-stage builds, container security and compose.
- CI/CD, environment promotion, rollback and infrastructure as code.
- Cost monitoring, right-sizing, backup and disaster recovery.

Resources: [AWS Skill Builder](https://skillbuilder.aws/), [AWS Well-Architected](https://docs.aws.amazon.com/wellarchitected/latest/framework/welcome.html).

## 9. Quality, security and operations

- Unit, integration, contract and end-to-end testing.
- Deterministic test data, test doubles and meaningful assertions.
- OWASP risks: injection, XSS, CSRF, SSRF and broken access control.
- Secure cookies, password hashing, secret handling and token lifecycle.
- Dependency scanning, SAST and container scanning.
- Logs, metrics, traces, SLI, SLO, error budgets and incident reviews.
- Profiling, load testing and capacity planning.

Resources: [OWASP Top 10](https://owasp.org/www-project-top-ten/), [Google SRE Book](https://sre.google/sre-book/table-of-contents/).

## 10. Technical leadership

- Technical discovery, requirements decomposition and estimation.
- Risk management, incremental delivery and stakeholder communication.
- Code review, mentoring, delegation and feedback.
- Architecture reviews, technical debt and decision records.
- Incident leadership and blameless postmortems.
- Aligning engineering decisions with product and business constraints.

## Portfolio evidence checklist

For each substantial project, publish a problem statement, non-goals, architecture diagram, ADRs, Docker-based setup, environment example without secrets, migrations, API docs, meaningful tests, CI workflow, security notes, operational considerations, known limitations and next steps.

## Capstone sequence

1. Modular NestJS API with TypeScript, PostgreSQL, authentication, RBAC and tests.
2. Refactor business logic behind ports and adapters; document module boundaries.
3. Add an asynchronous workflow with retries, idempotency and a dead-letter path.
4. Build a Next.js application with accessible forms and robust error states.
5. Deploy a small version to AWS with CI/CD, observability and cost controls.

The goal is not to collect technologies. The goal is to explain, implement, test, operate and evolve systems.

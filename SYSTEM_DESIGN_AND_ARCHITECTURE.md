# System Design & Architecture — Practical Reference

## 1. Start with requirements

Separate functional requirements (user-visible capabilities) from non-functional requirements (latency, throughput, availability, durability, security, privacy, scalability, maintainability and cost). Record constraints such as team size, deadlines, existing systems, compliance and budget.

Clarify traffic shape, peak-to-average ratio, payload size, read/write ratio, retention and recovery objectives before choosing components.

## 2. Repeatable design sequence

1. Define users, use cases and system boundaries.
2. Estimate scale with explicit assumptions.
3. Define APIs and important data entities.
4. Draw components and data flows.
5. Identify consistency and transaction requirements.
6. Define failure handling, security and observability.
7. Compare at least two plausible designs.
8. Record decisions and revisit them when constraints change.

## 3. Architecture styles

**Layered architecture:** separates presentation, application, domain and infrastructure. It is understandable, but dependencies become tangled if layers reach around each other.

**Hexagonal architecture (Ports and Adapters):** the application core defines ports; adapters implement HTTP, databases, queues and external APIs. The core should not depend on infrastructure frameworks.

**Modular monolith:** one deployable application with explicit module boundaries. Often a strong starting point when transactional simplicity matters and distributed-system overhead is not justified.

**Microservices:** independently deployable services around business capabilities. Use them when independent deployment, scaling or ownership is valuable enough to justify network failures, distributed data and operational complexity.

## 4. Domain-Driven Design essentials

- Ubiquitous language: use business terms consistently in code and conversation.
- Entity: identity matters over time.
- Value object: defined by its values; usually immutable.
- Aggregate: consistency boundary controlled through an aggregate root.
- Repository: collection-like abstraction for aggregate persistence.
- Domain service: domain operation that does not naturally belong to one entity.
- Domain event: fact that has occurred within the domain.
- Bounded context: explicit boundary where a model and language are consistent.
- Context map: relationships and integration between contexts.

Model invariants and meaningful business behaviour; do not create classes for every noun.

## 5. Distributed systems trade-offs

- Networks fail, time out and deliver delayed responses.
- A timeout does not prove the remote operation failed.
- Retries require idempotency and bounded backoff with jitter.
- At-least-once delivery requires duplicate-safe consumers.
- Ordering is usually guaranteed only within a defined partition or key.
- A transactional outbox helps publish events alongside database changes.
- Sagas coordinate long-running workflows with compensating actions.
- Eventual consistency needs explicit product behaviour.

## 6. Common building blocks

| Need | Options | Design questions |
|---|---|---|
| Synchronous request | REST, GraphQL, gRPC | Is request/response appropriate? |
| Async work | SQS, RabbitMQ, Kafka, EventBridge | Queue or stream? Ordering? Retention? |
| Cache | Redis, CDN, application cache | What is the invalidation strategy? |
| Relational data | PostgreSQL, MySQL | Constraints, transactions and query patterns? |
| Object storage | S3 | Access policy, encryption and lifecycle? |
| Search | OpenSearch, Elasticsearch | Is a dedicated search engine necessary? |
| Workflow | Step Functions, Temporal | How are retries and compensation handled? |

## 7. API design checklist

- Consistent resource naming and HTTP semantics.
- Explicit schemas and runtime validation.
- Pagination, filtering and sorting limits.
- Stable error format with correlation ID.
- Authentication and object-level authorisation.
- Rate limits, request size limits and timeouts.
- Idempotency for retryable writes.
- Versioning and backward-compatible evolution.
- OpenAPI documentation and contract tests.

## 8. Production-readiness checklist

- Health and readiness endpoints.
- Structured logs with request identifiers.
- Metrics for latency, traffic, errors and saturation.
- Distributed tracing across service boundaries.
- Timeouts on outbound calls.
- Retry budgets and circuit breaking where appropriate.
- Graceful shutdown and connection draining.
- Secrets outside source control.
- Backups with tested restore procedures.
- Actionable alerts, runbooks and cost monitoring.

## 9. Architecture Decision Record template

    # ADR-0001: Decision title
    - Status: Proposed | Accepted | Superseded
    - Date: YYYY-MM-DD

    ## Context
    What problem and constraints led to this decision?

    ## Decision
    What are we choosing?

    ## Alternatives
    What realistic options were considered?

    ## Consequences
    Benefits, costs, risks and operational impact.

    ## Follow-up
    How will we validate and revisit this decision?

## Further reading

- [C4 Model](https://c4model.com/)
- [AWS Well-Architected Framework](https://docs.aws.amazon.com/wellarchitected/latest/framework/welcome.html)
- [Martin Fowler — Architecture](https://martinfowler.com/architecture/)
- [Microsoft Cloud Design Patterns](https://learn.microsoft.com/en-us/azure/architecture/patterns/)

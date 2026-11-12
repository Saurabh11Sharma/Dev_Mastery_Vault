# Software Engineering Bookshelf & Reading Guide

A curated reading list for a senior JavaScript / TypeScript engineer growing toward technical leadership and software architecture. These are reading notes and study prompts, not reproductions of copyrighted chapters.

## Recommended reading order

| Order | Book | What to learn |
|---|---|---|
| 1 | [A Philosophy of Software Design — John Ousterhout](https://www.goodreads.com/book/show/39996759-a-philosophy-of-software-design) | Managing complexity, deep modules, information hiding and design clarity |
| 2 | [The Pragmatic Programmer — David Thomas & Andrew Hunt](https://pragprog.com/titles/tpp20/the-pragmatic-programmer-20th-anniversary-edition/) | Professional habits, feedback loops, automation and maintainability |
| 3 | [Designing Data-Intensive Applications — Martin Kleppmann](https://dataintensive.net/) | Transactions, replication, partitioning, streams and distributed-system trade-offs |
| 4 | [Refactoring — Martin Fowler](https://martinfowler.com/books/refactoring.html) | Safe code transformation, code smells and incremental design |
| 5 | [Domain-Driven Design Distilled — Vaughn Vernon](https://www.domainlanguage.com/ddd/) | Bounded contexts, ubiquitous language and strategic DDD |
| 6 | [Clean Architecture — Robert C. Martin](https://www.pearson.com/en-us/subject-catalog/p/clean-architecture-a-craftsmans-guide-to-software-structure-and-design/P200000000272/9780134494166) | Dependency direction, boundaries and trade-offs |
| 7 | [Fundamentals of Software Architecture — Mark Richards & Neal Ford](https://www.oreilly.com/library/view/fundamentals-of-software/9781492043447/) | Architecture characteristics, styles and decision-making |
| 8 | [Release It! — Michael T. Nygard](https://pragprog.com/titles/mnee2/release-it-second-edition/) | Production failure modes, resilience and operational design |
| 9 | [Site Reliability Engineering — Google](https://sre.google/sre-book/table-of-contents/) | SLIs, SLOs, monitoring and incident response |
| 10 | [Accelerate — Nicole Forsgren, Jez Humble & Gene Kim](https://itrevolution.com/product/accelerate/) | Delivery performance and engineering effectiveness |

## JavaScript and TypeScript

- [You Don't Know JS Yet — Kyle Simpson](https://github.com/getify/You-Dont-Know-JS): scope, closures, objects, types and asynchronous behaviour.
- [Effective TypeScript — Dan Vanderkam](https://effectivetypescript.com/): practical type-system guidance and safer APIs.
- [Programming TypeScript — Boris Cherny](https://www.oreilly.com/library/view/programming-typescript/9781492037644/): type modelling and application design.

Study questions: What does the compiler prove? What still needs runtime validation? How can types make invalid states harder to represent?

## Node.js and backend systems

- [Node.js Design Patterns — Mario Casciaro & Luciano Mammino](https://www.packtpub.com/): asynchronous patterns, streams and event-driven design.
- [API Security in Action — Neil Madden](https://www.manning.com/books/api-security-in-action): practical API security, authentication and authorisation.
- [Web API Design — Apigee](https://pages.apigee.com/rs/apigee/images/api-design-ebook-2012-03.pdf): resource modelling and API consistency.

Study questions: What blocks the event loop? When are streams better than buffering? How should an API handle retries, timeouts and idempotency?

## Architecture and domain modelling

- [Domain-Driven Design — Eric Evans](https://www.domainlanguage.com/ddd/): foundational DDD concepts; read after the distilled introduction.
- [Implementing Domain-Driven Design — Vaughn Vernon](https://www.domainlanguage.com/ddd/): tactical patterns and implementation guidance.
- [Patterns of Enterprise Application Architecture — Martin Fowler](https://martinfowler.com/books/eaa.html): domain models, data mapping and enterprise patterns.
- [Building Microservices — Sam Newman](https://samnewman.io/books/building_microservices_2nd_edition/): service boundaries, deployment, testing and operations.

Study questions: Is a microservice boundary justified? Who owns the data? What consistency guarantees does the workflow need?

## Databases and distributed systems

- [Designing Data-Intensive Applications — Martin Kleppmann](https://dataintensive.net/): core reference for data-intensive systems.
- [SQL Performance Explained — Markus Winand](https://sql-performance-explained.com/): indexes and query performance.
- [Database Internals — Alex Petrov](https://www.oreilly.com/library/view/database-internals/9781492040330/): storage engines, indexes and distributed database internals.

Study questions: What does the query plan show? Which index supports the predicate and ordering? What happens when a consumer processes an event twice?

## Cloud, operations and security

- [Cloud Native Patterns — Cornelia Davis](https://www.manning.com/books/cloud-native-patterns): patterns for cloud-native systems.
- [The Site Reliability Workbook — Google](https://sre.google/workbook/table-of-contents/): applying SRE practices.
- [Threat Modeling — Adam Shostack](https://shostack.org/books/threat-modeling-book): structured threat identification.
- [Security Engineering — Ross Anderson](https://www.cl.cam.ac.uk/~rja14/book.html): broad security engineering foundations.

## Frontend and product engineering

- [Designing Interfaces — Jenifer Tidwell, Charles Brewer & Aynne Valencia](https://www.oreilly.com/library/view/designing-interfaces-3rd/9781492051954/): interaction patterns and usability.
- [Refactoring UI — Adam Wathan & Steve Schoger](https://www.refactoringui.com/): visual hierarchy and interface refinement.
- Official references: [React](https://react.dev/learn), [Next.js](https://nextjs.org/docs), [web.dev](https://web.dev/learn/).

## How to convert reading into skill

For each chapter, write a one-page note containing: the problem being solved, the core mental model in your own words, a small Node.js / TypeScript example, trade-offs, one interview question and one experiment that validates your understanding.

Start with the first five books and apply each idea in code. Return to deeper references when a real engineering problem requires them. Do not try to read every book at once.

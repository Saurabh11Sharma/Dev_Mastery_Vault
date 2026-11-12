# AWS & Cloud Engineering — Practical Notes

## Core services for a Node.js engineer

| Service | Purpose | Engineering concerns |
|---|---|---|
| IAM | Identity and permissions | Roles, policies, least privilege and trust |
| VPC | Network isolation | Subnets, routes, security groups and endpoints |
| EC2 | Virtual machines | Patching, scaling, images and sizing |
| S3 | Object storage | Bucket policies, encryption, versioning and lifecycle |
| RDS | Managed relational database | Backups, connections, failover and maintenance |
| Lambda | Event-driven compute | Cold starts, timeouts, concurrency and package size |
| API Gateway | Managed API front door | Auth, throttling, validation and integration |
| SQS | Message queue | Visibility timeout, retries, DLQ and idempotency |
| SNS | Pub/sub notifications | Fan-out, subscriptions and delivery |
| EventBridge | Event routing | Schemas, filtering and loose coupling |
| Step Functions | Workflow orchestration | State, retries, catches and compensation |
| CloudWatch | Logs, metrics and alarms | Useful signals, retention and alert quality |
| CloudTrail | API activity history | Auditability and investigation |
| Secrets Manager | Secret storage and rotation | Access policies and rotation workflows |

## IAM and security

- Prefer workload roles over long-lived access keys.
- Grant the minimum permissions required.
- Restrict trust policies and resource policies.
- Encrypt data in transit and at rest where appropriate.
- Keep secrets out of Git, container images and build logs.
- Separate environments and accounts for meaningful isolation.
- Review public access settings on S3 and network resources.

## Serverless design

Consider Lambda when execution is event-driven, demand varies and operational simplicity is valuable.

Design for stateless handlers, explicit timeouts, bounded retries, idempotent processing, cold-start and concurrency behaviour, payload limits, database connection management, dead-letter queues, replay strategy and structured logs.

Do not use serverless merely because it is fashionable; compare workload shape, latency, operational model and cost.

## Messaging reliability

For SQS consumers, set visibility timeout longer than normal processing time, make handlers idempotent, configure bounded retries and a dead-letter queue, monitor age of oldest message and DLQ depth, and define safe replay procedures. Do not assume global ordering.

## Cost and reliability

- Tag resources consistently and set budgets.
- Right-size compute using observed metrics.
- Use S3 lifecycle rules for retained data.
- Review NAT gateway, data transfer and logging costs.
- Define backup and recovery objectives.
- Test restores and failover, not only backup creation.
- Use the AWS Well-Architected pillars as a review framework.

## Infrastructure as Code

Use AWS CDK, CloudFormation or Terraform. Keep infrastructure changes reviewed, versioned and deployable through CI/CD. Avoid manual production drift.

## Further resources

- [AWS Skill Builder](https://skillbuilder.aws/)
- [AWS Well-Architected Framework](https://docs.aws.amazon.com/wellarchitected/latest/framework/welcome.html)
- [AWS Architecture Center](https://aws.amazon.com/architecture/)
- [AWS Serverless Applications Lens](https://docs.aws.amazon.com/wellarchitected/latest/serverless-applications-lens/welcome.html)
- [AWS Security Best Practices](https://docs.aws.amazon.com/security/)

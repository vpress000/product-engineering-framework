# Production Operations and Reliability

## Operational ownership

Every production service or critical capability should have a named owner, support path, and documented operational expectations.

## Service objectives

Where appropriate, define service-level indicators and objectives for availability, latency, error rate, throughput, data freshness, and other user-visible behavior. Set targets based on user needs and business impact, not arbitrary industry numbers.

## Observability

Use logs, metrics, traces, dashboards, and alerts proportionate to system complexity. Alerts should be actionable, owned, and tuned to reduce noise. Monitor both technical health and important product journeys.

## Incident management

Define severity levels, incident roles, escalation paths, communications, mitigation, recovery, and post-incident review. Prioritize user safety and service restoration. Preserve relevant evidence and protect sensitive data.

## Resilience and recovery

Document dependencies, failure modes, backup frequency, recovery point objective (RPO), recovery time objective (RTO), and restore procedures where relevant. Test backups and recovery; a successful backup job is not proof that restoration works.

## Continuous operations

Review incidents, user feedback, capacity, vulnerabilities, dependency updates, cost, and operational toil. Feed improvements into the roadmap and engineering backlog.

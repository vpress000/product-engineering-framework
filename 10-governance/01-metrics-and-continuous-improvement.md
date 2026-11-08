# Metrics and Continuous Improvement

## Measurement principles

Use metrics to learn about the system and improve outcomes, not to rank individuals or maximize activity. Pair quantitative signals with qualitative context. Avoid targets that encourage gaming.

## Product outcome measures

Select measures tied to the product strategy, such as task success, adoption, retention, time-to-value, customer satisfaction, conversion, revenue/cost, or mission impact. Define measurement method and data limitations.

## Delivery and flow measures

Potential measures include lead time, cycle time, throughput, work in progress, blocked time, deployment frequency, and predictability. Interpret them as system signals, not individual productivity scores.

## Quality and reliability measures

Potential measures include escaped defects, change failure rate, restore time, incident frequency/severity, availability, latency, flaky test rate, and recurring defect patterns.

## Process health

Track process friction, rework, age of unresolved decisions, documentation freshness, review delay, and automation reliability where useful.

## Agentic asset measures (when applicable)

For material AI agents, skills, and prompt assets, measure task success against a defined task cohort, correctness/completeness, safety and permission adherence, regression rate, tool failures, latency, token/cost per completed task, human correction/rework, adoption, and deprecation/rollback events. Record asset version/hash, model/provider, tool configuration, evaluation manifest, and time window with the metric.

Do not compare assets across materially different task mixes or runtime configurations without qualification. Do not use invocation counts, session counts, or individual developer-level usage as productivity scores. Session-level measurement or harvesting requires an approved data boundary and retention policy. For behavior-changing improvements, use a pinned baseline, candidate evaluation, and controlled adoption process.

## Review loop

1. Define the question the metric is intended to answer.
2. Establish a baseline and data source.
3. Set an appropriate review cadence.
4. Examine trends and qualitative context.
5. Identify possible causes, not just correlations.
6. Agree an improvement experiment and owner.
7. Review results and adapt.

## Retrospectives

Focus on system conditions, not blame. Record what to continue, stop, improve, and experiment with. Assign owners and review actions. Revisit whether the framework itself is creating unnecessary overhead.

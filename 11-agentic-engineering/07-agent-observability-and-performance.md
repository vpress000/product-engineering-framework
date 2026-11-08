# Agent Observability and Performance Management

## Purpose

Measure whether agentic assets remain useful, reliable, safe, and economical after adoption, and whether SkillOpt-driven changes create durable improvements.

## Metric groups

| Dimension | Measures | Notes |
|---|---|---|
| Effectiveness | Task success, acceptance rate, first-pass completion | Segment by task family and skill version |
| Quality | Correctness, completeness, regression, defect escape | Use independent checks where possible |
| Reliability | Tool failures, timeouts, retries, incomplete outputs | Segment by backend/provider/environment |
| Safety | Policy violations, unauthorized access, sensitive-data incidents | Severe events are veto/incident signals |
| Efficiency | Tokens, cost/task, latency, tool calls, human rework | Include failed attempts and replay/reflection overhead |
| Adoption | Invocation, repeat use, active/deprecated versions | Low use may indicate low value or poor discoverability |
| Optimization quality | Candidate acceptance rate, gate failures, regression rate, held-out retention | Do not optimize for number of edits |
| Data quality | Task review rejection, duplicate rate, split contamination, missing outcomes | A low-quality task set invalidates performance claims |

## Attribution

Separate improvement from confounding changes in model/provider version, system prompt, task distribution, tool permissions, project architecture, test quality, and environment. Record each condition with the run. A held-out result supports only the tested configuration and task population.

## SkillOpt evidence

Research runs should preserve run config, skill versions, task manifests, split hashes, model/backend, history, and best candidate artifacts. Sleep runs should preserve reviewed task provenance, report, structured diagnostics, staging proposal, and cost. Use the current repository's artifact layout as authoritative. Keep logs sensitive and apply retention controls.

## Review cadence

Start with a manual review after each candidate adoption and periodic/event-triggered checks after model, provider, codebase, API, or permission changes. Schedule ongoing Sleep only when the data source, provider, retention, and budget are approved.

## Reporting

Distinguish observed facts, estimates, uncertainty, qualitative feedback, and hypotheses. Report task-level breakdowns, critical regressions, cost, and failure modes. Do not claim durable improvement from a mock run, one benchmark, a single successful task, or the number of skills generated.

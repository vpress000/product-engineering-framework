# SkillOpt Data Governance, Security, and Cost Controls

## Purpose

Control the data, permissions, external model calls, local artifacts, and cost created by SkillOpt research and Sleep workflows.

## Data inventory

Before use, classify each input/output:

- raw coding-agent transcripts;
- harvested session digests and mined task records;
- issue/requirement text and code excerpts;
- repository source, diffs, tests, fixtures, and logs;
- optimizer/reflection prompts and replies;
- run evidence logs and diagnostics;
- baseline/candidate skills and evaluation reports;
- staged proposals, backups, receipts, and task archives.

Classify each as public, internal, confidential, regulated, or restricted according to the product's policy. Do not send restricted data to an external provider unless explicitly authorized by the responsible owner and contractual/privacy controls.

## SkillOpt-Sleep data boundary

The reviewed Microsoft docs state that harvesting is local and read-only, but a real backend can send truncated transcript excerpts and derived tasks to the selected provider for mining, replay, judging, and reflection. Outbound prompts are not guaranteed to be free of secrets. Inspect and redact task records before real-backend replay. Known-pattern redaction is defense in depth, not a guarantee.

Evidence logs may retain copies of prompts and replies. Treat them as sensitive. Check whether evidence logging is enabled, where state/staging are written, how long data is retained, and who can read it. Avoid storing raw transcripts in PEOF documentation or the product repo.

## Minimum controls

1. Start with a mock/no-provider mode to inspect the local workflow.
2. Harvest only the chosen project/source and minimum time window.
3. Inspect, minimize, and redact transcript-derived tasks before provider use.
4. Exclude secrets, tokens, private keys, passwords, personal data, customer data, and production identifiers.
5. Use synthetic or sanitized repositories and fixtures for initial experiments.
6. Select a provider approved for the data classification; review retention, training, regional processing, and contractual terms.
7. Keep credentials in the approved secret store/environment, never in YAML, prompts, manifests, Git, or reports.
8. Turn off or restrict evidence logging if its contents are not needed; if retained, protect and expire it.
9. Apply least-privilege backend tools and filesystem permissions.
10. Do not run against production systems or production credentials.
11. Never auto-adopt on the basis of a score alone.

## Budget and time controls

Set small session/task/rollout limits during pilots and a documented token/cost threshold. Understand the current SkillOpt budget semantics: a budget may be checked before steps begin but a step already in progress may complete above the configured threshold. CLI backends may estimate token usage; not every mining/reflection call is counted identically across backends. Do not describe a soft token budget as a hard financial cap. Confirm provider spend controls separately.

Record expected and actual:

- input/output tokens and provider-reported usage where available;
- per-task and total cost estimate;
- elapsed duration;
- task/session counts;
- number of model calls and retries;
- skipped work caused by limits.

Stop if costs are unbounded, telemetry is missing, or the provider account cannot be constrained sufficiently for the planned pilot.

## Prompt injection and untrusted data

Treat transcripts, issue content, commit messages, repo files, test fixtures, web pages, model responses, and tool outputs as untrusted input. They may contain hostile instructions. They must never override the evaluation policy, tool allowlist, approval requirements, or system/developer instructions. Do not execute instructions copied from transcripts or repository content without independent review.

## Retention and deletion

Define a retention period for transcripts, task archives, evidence logs, run outputs, and backups. Store only what is required to reproduce the decision. Document deletion actions and confirm that scheduled jobs do not recreate deleted archives unexpectedly.

## Incident response

If a secret or restricted data may have been transmitted, stop the workflow, preserve relevant audit metadata without spreading the secret, notify the data owner/security contact, follow credential rotation and incident procedures, and review provider logs/retention options. Do not continue optimization until cleared.


## Claude subscription allowance is a separate operating constraint

When SkillOpt invokes Claude through a subscription-backed Claude Code workflow, model-backed benchmark runs, candidate generation, replay, and parallel workers can consume the same account allowance used by Claude's other surfaces. This is distinct from any API/provider charges, CI charges, and local compute costs.

Before a real-model run, follow [`../13-usage-efficiency/09-skillopt-and-agentic-workload-budgeting.md`](../13-usage-efficiency/09-skillopt-and-agentic-workload-budgeting.md) and complete [`../09-templates/38-skillopt-run-budget-template.md`](../09-templates/38-skillopt-run-budget-template.md). Use a small pilot, one skill at a time, low concurrency, explicit task/iteration caps, and manual approval before expanding. Do not enable usage credits or API billing automatically. A locally installed SkillOpt repository does not make model-backed optimization free.

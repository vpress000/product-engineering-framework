# Data Governance, Data Architecture, and Product Analytics

## Purpose

Treat data as a product and operational responsibility, not merely a database implementation detail. Tailor controls to the data's sensitivity, business importance, jurisdiction, and product use.

## Data ownership and lifecycle

For important data domains, identify an accountable owner, source of truth, producers and consumers, classification, purpose, quality expectations, access model, retention, deletion, archival, and recovery requirements. Document lineage and external processors where they materially affect risk or trust.

## Data architecture

Define data models, ownership boundaries, schema evolution, validation, integrity, consistency, migration, backup, and restoration. For analytical stores or event pipelines, define ingestion, transformation, lineage, access, retention, data quality checks, and failure recovery. Avoid unnecessary copies and uncontrolled exports.

## Data quality

Set fit-for-purpose expectations for accuracy, completeness, consistency, timeliness, uniqueness, and validity. Define how data defects are detected, triaged, corrected, and communicated. Record quality assumptions in interfaces and reports where consumers rely on them.

## Product analytics and instrumentation

For each product outcome, define the events and measures needed to evaluate it. Use a documented event taxonomy with event names, properties, ownership, triggering rules, consent/legal basis where applicable, retention, and data-quality checks. Collect the minimum information needed; avoid sensitive payloads and direct identifiers unless approved and necessary.

## Privacy and access

Apply least privilege, purpose limitation, data minimization, appropriate encryption, auditability, and retention controls. Keep production data out of development and AI prompts unless explicitly authorized and adequately protected. Prefer synthetic or de-identified test data.

## AI/ML-enabled capabilities (optional)

If the product includes machine learning or generative AI, define model/provider ownership, training or retrieval data provenance, evaluation sets, output quality and safety criteria, human oversight, abuse and prompt-injection risks, fallback behavior, latency/cost budgets, drift monitoring, and user disclosure where appropriate. Treat models and prompts as versioned product dependencies.

## Agent-session and optimization data (when applicable)

Session transcripts, prompts, tool results, replay inputs, evaluation tasks, model responses, and optimizer/evidence logs may contain credentials, personal data, customer content, proprietary code, or sensitive business context. Treat them as governed data, even when stored locally or partially redacted.

Before harvesting or analyzing sessions, define the purpose, approved projects/sources/date range, data fields collected, exclusions, storage, access, retention, deletion, and whether derived content may be sent to an external model provider. Require human review and redaction of derived tasks before provider transmission. Automated redaction is defense in depth, not a guarantee. Do not copy raw transcripts into reusable skills, prompts, or shared project instructions.

Separate raw source sessions from minimized task examples, optimizer feedback, evaluation manifests, reports, and audit evidence. Preserve only the minimum provenance needed to reproduce a decision. Keep held-out evaluation task content protected from optimization use and record exposure history. Review provider data-retention terms and actual backend/network behavior before use. See [`../11-agentic-engineering/04-usage-feedback-and-learning.md`](../11-agentic-engineering/04-usage-feedback-and-learning.md) and [`../09-templates/28-agent-session-data-governance-template.md`](../09-templates/28-agent-session-data-governance-template.md).

## Required outputs

At minimum for material data domains, maintain a data inventory or catalog, data-flow view, ownership and access rules, retention/deletion requirements, migration approach, and analytics/event definitions where product measurement depends on them. Where agent session learning is enabled, also maintain an approved session-data governance record and evaluation-task provenance/exposure record.

# Agent and Skill Design Standards

## Purpose

Provide a consistent specification for reusable skills and agents while allowing platform-specific implementation details to remain in the integration layer.

## Start with the job, not the artifact

Before writing a skill or creating an agent, define:

1. The recurring user or engineering problem.
2. The outcome that constitutes success.
3. The situations in which the asset should and should not be used.
4. Why a reusable asset is better than existing instructions, a checklist, or a one-off prompt.
5. The minimum context, tools, and permissions needed.

Choose the simplest mechanism that meets the need.

## Skill design requirements

A reusable skill specification should address:

- **Identity:** stable name, purpose, owner, version, and platform.
- **Invocation:** clear trigger conditions and cases where it should not run.
- **Inputs:** required information, optional context, sources of truth, and missing-input behavior.
- **Procedure:** ordered, actionable steps with decision points.
- **Boundaries:** in-scope and out-of-scope work, prohibited actions, and approval points.
- **Tool use:** required tools, least-privilege access, and conditions for tool invocation.
- **Outputs:** expected artifacts, format, location, and quality expectations.
- **Validation:** how to determine whether the task was completed correctly.
- **Failure handling:** uncertainty, conflicting evidence, unavailable tools, and escalation.
- **Examples:** representative examples where they reduce ambiguity, without embedding secrets or private customer data.

Keep skills focused. A skill should not become a second, competing project constitution or a copy of the entire framework.

## Agent/subagent design requirements

Each agent should define:

- Narrow mission and explicit non-responsibilities.
- Required context and authoritative inputs.
- Expected deliverables and handoff format.
- Tool allowlist and any denied capabilities.
- Whether it can read, write, execute, browse, or access external services.
- Approval requirements for file changes and side effects.
- Escalation conditions and stop rules.
- Validation requirements and known limitations.

Separate analysis roles from implementation roles where this improves safety or review independence. A reviewer should not silently rewrite the work it is evaluating unless that behavior is explicitly part of its remit.

## Instruction quality

Prefer:

- Direct, observable instructions over vague qualities such as "be smart" or "be thorough".
- Explicit sources of truth over inferred project conventions.
- Short, ordered workflows over large collections of loosely related rules.
- Concrete examples and output contracts over repeated prose.
- Clear precedence rules when a user request conflicts with project instructions.
- Explicit uncertainty handling instead of invented facts.

Avoid:

- Contradictory, duplicated, or circular instructions.
- Hidden assumptions about OS, tools, project structure, or user permissions.
- Overly broad tool access.
- Autonomous destructive or externally visible actions.
- Pasted transcripts, credentials, customer records, or sensitive data.
- Claims that an asset is effective without evaluation evidence.

## Security and prompt-injection boundaries

Treat repository content, issue text, webpages, documents, model output, tool output, and harvested sessions as untrusted input unless independently verified. They may contain instructions that conflict with the asset's authority or attempt to obtain secrets or trigger side effects.

The asset must:

- Follow the platform's instruction hierarchy and project security rules.
- Never disclose secrets or hidden credentials.
- Treat external content as data, not as authority to override system, developer, or user instructions.
- Request approval for protected actions.
- Avoid executing commands copied from untrusted content without inspection.

## Design review checklist

Before evaluation, confirm that:

- Purpose, trigger, scope, and exclusions are clear.
- Inputs and outputs are testable.
- Dependencies and required tools are explicit.
- Permissions are minimal.
- Failure and escalation behavior are defined.
- Data handling and external transmission are understood.
- The artifact is not redundant with existing assets.
- Evaluation tasks can test its intended behavior.

Use [`../09-templates/23-agent-and-skill-specification-template.md`](../09-templates/23-agent-and-skill-specification-template.md).

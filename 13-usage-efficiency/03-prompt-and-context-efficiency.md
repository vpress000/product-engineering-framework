# Prompt and Context Efficiency

## Purpose

Keep the information Claude must process relevant, concise, and reusable. This supports subscription efficiency and output quality.

## 1. Prompt once with a complete task brief

A high-quality first prompt should include:

- Desired outcome.
- Relevant product/feature group.
- Scope and explicit exclusions.
- Source-of-truth paths.
- Constraints and approved decisions.
- Acceptance criteria.
- Validation commands, if known and safe.
- Expected completion report.

Avoid a chain of avoidable clarifications caused by missing information. Do not turn the initial prompt into a full product history; link to the relevant project records.

## 2. Keep always-loaded instructions lean

`CLAUDE.md` is read broadly and can influence each turn. Keep it concise and limited to durable project context, essential rules, quality commands, and links to deeper references. Put workflow-specific instructions in on-demand skills and directory-specific rules in scoped rule files.

PEOF guidance: do not load the complete PEOF library at every session start. Use the framework index, determine which discipline applies, and load only those documents.

## 3. Retrieve selectively

- Identify the relevant source-of-truth document before reading large folders.
- Ask Claude to inspect specific files or symbols when known.
- Prefer targeted search with a narrow path and pattern over a broad recursive search.
- Avoid re-reading files already present in the current context unless they changed or need verification.
- For large logs, provide a small relevant excerpt and preserve the full log on disk.
- Avoid pasting entire source files, lockfiles, generated bundles, database dumps, or long command output.
- Use a plain file path when selective reading is desired; check current Claude Code guidance before using `@` file mentions because they may attach the full file content.

## 4. Keep command output small

Use appropriate quiet/summary flags, focused test selection, bounded log tails, and machine-readable summaries where they genuinely reduce noise. Do not hide warnings or failures needed for verification. Store full output in a file when necessary and return only the relevant excerpt and path.

## 5. Avoid context duplication

- Do not include the same architecture or requirements content in `CLAUDE.md`, PRD, SRS, TDD, and prompt text.
- Reference the canonical file instead.
- Do not attach the same large file repeatedly in one session.
- Do not ask Claude to print a file it has already read unless a human-readable extract is the deliverable.
- Prefer diffs and summaries over full-file reprints.

## 6. Prompt caching awareness

Claude Code manages prompt caching. Stable session configuration and repeated prompt prefixes can help cache reuse. Anthropic's published guidance warns that changing model, effort, or Fast mode in the middle of a session can invalidate cached prompt state and trigger more prefill work. Set intended model/effort near session start when practical. Do not avoid a necessary model change solely to preserve a cache; correctness takes priority.

Caching reduces repeated processing but does not make long or irrelevant context free, and it does not reset subscription limits.

## 7. Output discipline

Ask for the deliverable in the format that is useful: a patch, concise table, named file, or short report. Avoid asking for exhaustive reasoning transcripts or repeated summaries. Require enough evidence to validate the result, not a verbose narration of every internal step.

## Official references

- [Maximizing the value of Claude Code sessions](https://claude.com/resources/articles/maximizing-the-value-of-your-claude-code-sessions)
- [Models, usage, and limits in Claude Code](https://support.claude.com/en/articles/14552983-models-usage-and-limits-in-claude-code)

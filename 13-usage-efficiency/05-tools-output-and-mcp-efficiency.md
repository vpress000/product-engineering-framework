# Tool Output and MCP Efficiency

## Purpose

Prevent low-value tool calls and noisy outputs from consuming subscription capacity and crowding out the actual engineering task.

## 1. Discover once, then work from evidence

- Use the project inventory and prior handoff before repeating repository discovery.
- Search within likely directories before searching the entire repository.
- Read the smallest relevant range or file set.
- Use existing test names, stack traces, file paths, and symbols to target investigation.
- Do not repeatedly run the same broad search because the first result was not summarized.

## 2. Command output policy

For shell commands and tools:

- Prefer summaries, quiet flags, test filters, and bounded output where supported.
- Avoid dumping entire dependency trees, generated directories, coverage files, or full build logs into the conversation.
- Preserve detailed logs in files when needed for audit, but surface only the lines relevant to the current decision.
- Never suppress a failure merely to reduce output.
- Avoid repeated build/test runs when no code or configuration changed.

## 3. MCP and integrations

MCP server definitions and tool schemas can add startup/context overhead. Enable only integrations needed for the current task. If a server is not needed, disable or omit it according to current supported configuration rather than loading every connected tool into every session.

Before connecting an external service, check permissions, data sent, authentication, and whether it is required. Do not invoke external integrations merely because they are available.

## 4. File mention guidance

Anthropic's guidance has evolved around file references and direct mentions. When optimizing subscription usage, prefer a selective read of the specific symbol or range where that reduces payload. Use `@` mentions only when direct attachment is desirable and the file is not large; do not repeatedly attach the same file.

## 5. Test efficiency

Use a test pyramid:

1. Run the most targeted relevant test first.
2. Run adjacent integration tests after a change to shared behavior.
3. Run full regression/build checks at the agreed quality gate, not after every trivial edit.
4. Capture exact command, exit status, and concise result.

Never skip required testing just to conserve quota. Instead scope the implementation and test plan proportionately.

## 6. External work and cost

Before any workflow that makes paid external calls, triggers CI minutes, creates resources, or sends data, identify the side effect and obtain approval under project policy. Subscription usage and external service charges are separate concerns.

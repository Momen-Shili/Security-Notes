# Prompt injection in AI agents

**Risk:** text the agent reads (an email, web page, tool result, PDF) contains instructions, and the model follows them. The attacker never talks to your agent directly. This is called indirect prompt injection.

## What can go wrong
Leaking data, calling tools the user never asked for, changing the answer, or sending data out through a URL or markdown image.

## Defences that help (use several)
1. **Separate trusted from untrusted:** put external content in a labelled data block and tell the model it is never an instruction. This reduces risk but does not eliminate it.
2. **Least privilege:** give the agent only the tools it needs, with narrow permissions.
3. **Human confirmation** for destructive or outbound actions (send, delete, pay).
4. **Do not auto-render model-written URLs or images,** which can carry data out.
5. **Verifier step:** a second check compares the final answer and tool calls with the user's original request.
6. **Normalise input** (Unicode, encodings) before filtering, and do not rely on keyword blocklists alone: they miss other languages, encodings and obfuscation.
7. **Do not mix secrets and untrusted content** in the same context when you can avoid it.

## Testing
Treat it like a regression test: [agent-injection-tests](https://github.com/Momen-Shili/agent-injection-tests) runs inert payloads through several carriers and reports resistance and whether the real task still completes. Passing means it resisted known styles, not that it is safe.

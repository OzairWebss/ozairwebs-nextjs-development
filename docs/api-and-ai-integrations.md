# API and AI integration contracts

A successful integration defines who owns the data, what each side may do and how failures are reconciled. Start with a contract containing identifiers, authentication, payload validation, timeouts, rate limits, retry behaviour and audit requirements. A successful API call does not prove that a business operation completed correctly.

## Webhooks and background work

Verify provider signatures using the provider's documented method and the required request representation. Persist or queue accepted events with stable identifiers. Handle duplicates and out-of-order messages. Exponential retry needs a ceiling and a reconciliation route; uncontrolled retry can repeat a payment or exhaust a dependency.

For CRM, ERP, email and WhatsApp Business API work, confirm provider access and supported permissions first. n8n can coordinate approved steps, while the application enforces its own record permissions. Keep secrets server-side and treat incoming files and messages as untrusted data.

## Model-assisted operations

OpenAI, Anthropic and Gemini support different model/tool capabilities. Inspect current provider documentation instead of assuming identical schemas, refusal states or streaming events. Structured output can improve parsing, but validate values and business rules before using it. Tool selection is a model proposal; actual execution belongs to the application.

In RAG, store approved sources with version/provenance and filter retrieval by permission. Apply deletion and retention policies to embeddings and source text. A vector result's similarity does not make it authorised or factually correct. Test malicious retrieved instructions and stale material.

Use separate read and write tools. Require the relevant human approval for publication, refunds or sensitive external communication. Give MCP clients only the intended tool surface and record the acting identity. The [MCP security guidance](https://modelcontextprotocol.io/specification/latest/basic/security_best_practices) provides a protocol reference; it does not certify a particular deployment.

## Acceptance tests and operating limits

Test provider downtime, malformed arguments, duplicate events, revoked credentials, cancellation during streaming and exhausted quotas. Track model tokens/cost, latency and failures without retaining unnecessary prompt contents. Define a helpful manual fallback.

Read the primary references for [OpenAI tool calling](https://platform.openai.com/docs/guides/function-calling), [structured outputs](https://platform.openai.com/docs/guides/structured-outputs), [Claude tools](https://docs.anthropic.com/en/docs/build-with-claude/tool-use/overview) and [Gemini function calling](https://ai.google.dev/gemini-api/docs/function-calling). Examples here are scoped designs, not executable production integrations or claims of completed client work.

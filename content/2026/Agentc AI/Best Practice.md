**Best Practices for AI Tool Calls**

- Validate all inputs before sending to tools.
- Use structured error handling (try/except).
- Retry transient failures with exponential backoff.
- Log errors and attempts for debugging.
- Return safe fallback results to GPT to keep responses graceful.
- Avoid infinite loops; set max retries and timeouts.4

Transient failures are **temporary issues** such as:

- Network timeouts
- Database connection drops
- API rate limits (HTTP 429)
- Server temporarily unavailable (HTTP 503)
- delay = baseDelay \* (2 ^ retryCount)

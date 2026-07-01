## 2024-05-19 - WebSocket Batch Writing Optimization
**Learning:** In asyncio stream handlers, calling `writer.write()` inside a loop incurs significant Python-level overhead and transport buffer manipulation. Using a generator inside `b''.join()` to concatenate payloads into a single byte string before calling `write()` substantially minimizes this overhead for batched messages.
**Action:** Whenever iterating to write byte streams in Python, aggregate them into a single write buffer where memory constraints permit.

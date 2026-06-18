## 2024-05-18 - asyncio stream `writer.write()` overhead
**Learning:** Calling `writer.write()` inside a loop for `asyncio` streams introduces significant overhead due to multiple trips through the event loop and multiple internal buffer appends.
**Action:** When sending a batch of payloads, favor joining the bytes (`b''.join(...)`) into a single byte string and using a single `writer.write()` call. This optimizes batching performance.

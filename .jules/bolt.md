## 2024-05-15 - [Python Asyncio Stream Writes]
**Learning:** In Python asyncio streams, calling `writer.write()` inside a loop for multiple chunks of data can be an anti-pattern as it incurs overhead for each write call.
**Action:** Favor joining bytes (`b''.join(...)`) into a single string/bytes object and calling `writer.write()` once for optimal batching performance.

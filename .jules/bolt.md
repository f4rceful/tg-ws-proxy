## 2024-05-26 - Asyncio Stream Batching
**Learning:** In Python asyncio streams, calling `writer.write()` in a loop is an anti-pattern for performance because it introduces significant overhead for multiple system calls and context switches.
**Action:** Always favor joining bytes (`b"".join(...)`) into a single `writer.write()` call when sending batches of data.

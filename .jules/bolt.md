## 2024-05-18 - Asyncio Stream Batching Optimization
**Learning:** In Python asyncio streams, calling `writer.write()` inside a loop for many small frames incurs overhead from repeated stream operations, which can degrade performance.
**Action:** When writing multiple frames or parts to an asyncio stream, join them into a single byte string (e.g., using `b"".join(...)`) and use a single `writer.write()` call for optimal batching performance.

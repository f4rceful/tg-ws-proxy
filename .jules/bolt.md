## 2024-06-08 - Asyncio Stream Write Batching
**Learning:** In Python asyncio streams, calling `writer.write()` inside a loop for batched payloads generates high overhead. It is significantly more performant to construct a single `bytes` object (e.g., using `b''.join(...)`) and perform a single `writer.write()` call, rather than looping `write()` calls or using `writelines()`.
**Action:** When handling batch payload sends in Python asyncio, consistently join the bytes in memory first and do a single write to the writer to maximize throughput.

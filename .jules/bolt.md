## 2025-07-05 - Batch asyncio stream writes
**Learning:** In Python asyncio streams, favor joining bytes (`b''.join(...)`) into a single `writer.write()` call rather than looping `write()` calls or using `writelines()` for optimal batching performance.
**Action:** Always batch writes in loops using `b"".join()` when performance is critical.

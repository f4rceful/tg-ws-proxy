## 2024-07-07 - Asyncio Stream Write Batching
**Learning:** In Python asyncio streams, favor joining bytes (`b"".join(...)`) into a single `writer.write()` call rather than looping `write()` calls or using `writelines()` for optimal batching performance.
**Action:** Use `b"".join()` to concatenate bytes before calling `writer.write()`.

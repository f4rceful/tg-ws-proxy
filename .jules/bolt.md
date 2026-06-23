## 2024-06-23 - Asyncio Stream Write Batching
**Learning:** In Python asyncio streams, favor joining bytes (`b''.join(...)`) into a single `writer.write()` call rather than looping `write()` calls or using `writelines()` for optimal batching performance.
**Action:** Always combine bytes before calling `write()` when writing multiple parts to an asyncio stream.

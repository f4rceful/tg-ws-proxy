## 2024-06-09 - [Asyncio Stream Batching]
**Learning:** In Python asyncio streams, favor joining bytes (`b''.join(...)`) into a single `writer.write()` call rather than looping `write()` calls or using `writelines()` for optimal batching performance.
**Action:** Consolidate multiple `write()` calls into a single `write()` call using `b''.join()` when sending a batch of parts over an asyncio stream.

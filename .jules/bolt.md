## 2024-05-24 - [Asyncio Stream Batching]
**Learning:** In Python asyncio streams, looping `writer.write()` calls has overhead. Using `writer.writelines()` can also be suboptimal depending on the implementation.
**Action:** Favor joining bytes (`b''.join(...)`) into a single `writer.write()` call for optimal batching performance when writing multiple frames/chunks.
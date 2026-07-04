## 2024-07-04 - asyncio Stream Batching Performance
**Learning:** In Python asyncio streams, favor joining bytes (`b''.join(...)`) into a single `writer.write()` call rather than looping `write()` calls or using `writelines()` for optimal batching performance.
**Action:** Always batch multiple writes into a single `write()` call using `b''.join()` when sending multiple chunks of data sequentially over an asyncio stream.
